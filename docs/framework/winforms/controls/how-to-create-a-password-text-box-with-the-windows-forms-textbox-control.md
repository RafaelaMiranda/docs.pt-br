---
title: 'Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: 56391777c75db288c33d1b2192355be0df50f7ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046117"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms

Uma caixa de senha é uma caixa de texto do Windows Forms que exibe caracteres de espaço reservado enquanto um usuário digita uma cadeia de caracteres.

### <a name="to-create-a-password-text-box"></a>Criar uma caixa de texto de senha

1. Defina a <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriedade <xref:System.Windows.Forms.TextBox> do controle como um caractere específico.

    A <xref:System.Windows.Forms.TextBox.PasswordChar%2A> propriedade especifica o caractere exibido na caixa de texto. Por exemplo, se você quiser que os asteriscos sejam exibidos na caixa senha, especifique * <xref:System.Windows.Forms.TextBox.PasswordChar%2A> para a propriedade na janela Propriedades. Em seguida, independentemente de qual caractere de um usuário digita na caixa de texto, será exibido um asterisco.

2. Adicional Defina a <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> propriedade. A propriedade determina quantos caracteres podem ser digitado na caixa de texto. Se o tamanho máximo for excedido, o sistema emitirá um aviso sonoro e a caixa de texto não aceitará mais caracteres. Observe que isso pode não ser recomendável, visto que o tamanho máximo de uma senha pode ser útil para os hackers que estão tentando adivinhá-la.

    O exemplo de código a seguir mostra como inicializar uma caixa de texto que aceita uma cadeia de até 14 caracteres e exibir os asteriscos no lugar da cadeia de caracteres. O `InitializeMyControl` procedimento não será executado automaticamente; ele deve ser chamado.

    > [!IMPORTANT]
    > O uso <xref:System.Windows.Forms.TextBox.PasswordChar%2A> da propriedade em uma caixa de texto pode ajudar a garantir que outras pessoas não poderão determinar a senha de um usuário se observarem o usuário inserindo-a. Essa medida de segurança não abrange nenhum tipo de armazenamento e transmissão de senha que pode ocorrer devido a lógica do aplicativo. Como o texto inserido não é criptografado de nenhuma forma, você deve tratá-lo como qualquer outro dado confidencial. Mesmo que ela não apareça como tal, a senha é ainda está sendo tratada como uma cadeia de caracteres de texto sem formatação (a menos que você implemente alguma outra medida de segurança adicional).

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextBox>
- [Visão geral do controle TextBox](textbox-control-overview-windows-forms.md)
- [Como: Controlar o ponto de inserção em um controle de caixa de texto Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Como: Criar uma caixa de texto somente leitura](how-to-create-a-read-only-text-box-windows-forms.md)
- [Como: Colocar aspas em uma cadeia de caracteres](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Como: Selecionar texto no controle de caixa de texto Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como: Exibir várias linhas no controle de caixa de texto Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
