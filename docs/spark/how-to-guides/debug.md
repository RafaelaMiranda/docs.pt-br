---
title: Depurar um aplicativo .NET para Apache Spark no Windows
description: Saiba como depurar seu aplicativo .NET para Apache Spark no Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206150"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Depurar um aplicativo .NET para Apache Spark

Este guia de instruções fornece os comandos de que você precisa executar para depurar o aplicativo .NET para Apache Spark e código Scala no Windows.

## <a name="debug-your-application"></a>Depurar seu aplicativo

Abra uma nova janela do prompt de comando e execute o seguinte:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Quando você executa o comando, você vê a seguinte saída:

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

Nesse modo de depuração, o `DotnetRunner` não inicia o aplicativo .NET, mas aguarda até que ele se conecte. Deixe essa janela do prompt de comando aberta.

Agora você pode executar o aplicativo .NET com qualquer depurador para depurar seu aplicativo.

## <a name="debug-scala-code"></a>Depurar código Scala

Se você precisar depurar o código do lado do Scala, como `DotnetRunner` ou `DotnetBackendHandler`, execute o seguinte comando:

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Após executar o comando, anexe um depurador ao processo em execução usando o [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao .NET para Apache Spark](../tutorials/get-started.md)
* [Implantar um aplicativo .NET para Apache Spark no Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Implantar um aplicativo .NET para Apache Spark no Databricks](../tutorials/databricks-deployment.md)
* [Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
