---
title: Treinar novamente um modelo
description: Saiba como treinar novamente um modelo no ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 1628d0669d8a9e677ff39b5869d3802d89d96410
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397708"
---
# <a name="re-train-a-model"></a>Treinar novamente um modelo

Saiba como treinar novamente um modelo de machine learning no ML.NET.

O mundo e os dados ao redor dele mudam a um ritmo constante. Dessa forma, os modelos precisam mudar e se atualizar também. O ML.NET fornece funcionalidade para treinar novamente os modelos usando parâmetros de modelo aprendidos como um ponto de partida para criar continuamente com base em experiência anterior em vez de começar do zero toda vez.  

Os seguintes algoritmos podem ser treinados novamente do ML.NET:

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionTrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Carregar modelo pré-treinado

Primeiro, carregue o modelo pré-treinado no seu aplicativo. Para saber mais sobre como carregar modelos e pipelines de treinamento, veja o [artigo de instruções](./consuming-model-ml-net.md) relacionado.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Extrair os parâmetros de modelo pré-treinado

Depois que o modelo é carregado, extraia os parâmetros do modelo aprendido acessando a propriedade [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) do modelo pré-treinado. O modelo pré-treinado foi treinado usando o modelo de regressão linear [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) que cria um[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) que gera [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Esses parâmetros de modelo de regressão linear contêm o desvio aprendido e os pesos ou os coeficientes do modelo. Esses valores serão usados como ponto de partida para o novo modelo treinado novamente.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Treinar novamente o modelo

O processo de treinar novamente um modelo não é diferente daquele de treinar um modelo. A única diferença é que o método [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*), além dos dados, também utiliza como entrada os parâmetros de modelo aprendidos originais e os usa como um ponto de partida no processo de novo treinamento.  

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel = 
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a>Comparar parâmetros de modelo

Como você saberá se o novo treinamento realmente aconteceu? Uma maneira seria comparar se os parâmetros do modelo treinado novamente são diferentes do modelo original. O exemplo de código a seguir compara o original em relação os pesos do modelo treinado novamente e envia a saída ao console.

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs = 
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

A tabela a seguir mostra como poderia ser a saída. 

|Original | Treinado novamente | Diferença |
|---|---|---|
| 33039,86 | 56293,76 | -23253,9 |
| 29099,14 | 49586,03 | -20486,89 |
| 28938,38 | 48609,23 | -19670,85 |
| 30484,02 | 53745,43 | -23261,41 |
