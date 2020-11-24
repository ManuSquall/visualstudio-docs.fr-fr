---
title: Créer un éditeur de corps HTTP pour un test de performances de site Web
description: Découvrez comment créer un éditeur de contenu personnalisé qui vous permet de modifier le contenu du corps de chaîne ou le contenu de corps binaire d’une requête de service Web.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d6da75b24a982c420b475815f665851ebf06504
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440134"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Guide pratique pour créer un éditeur de corps HTTP personnalisé pour l’éditeur de test de performances web

Vous pouvez créer un éditeur de contenu personnalisé permettant de modifier le contenu du corps de type chaîne ou du corps binaire d’une demande de service web, de type SOAP, REST, asmx, wcf, RIA ou autre.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez implémenter ces types d'éditeurs :

- **Éditeur de contenu de chaîne** Ceci est implémenté à l’aide de l’interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>.

- **Éditeur de contenu binaire** Ceci est implémenté à l’aide de l’interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

Ces interfaces sont contenues dans l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

## <a name="create-a-windows-control-library-project"></a>Créer un projet de bibliothèque de contrôles Windows

1. Dans Visual Studio, créez un projet de **bibliothèque de contrôles Windows Forms**. Nommez le projet **MessageEditors**.

   Le projet est ajouté à la nouvelle solution et un <xref:System.Windows.Forms.UserControl> nommé *UserControl1.cs* est présenté dans le concepteur.

1. Dans la **Boîte à outils**, sous la catégorie **Contrôles communs**, faites glisser un <xref:System.Windows.Forms.RichTextBox> sur la surface de UserControl1.

1. Sélectionnez le glyphe de l’étiquette d’action (![Glyphe d’étiquette active](../test/media/vs_winformsmttagglyph.gif)) en haut à droite du contrôle <xref:System.Windows.Forms.RichTextBox>, puis sélectionnez **Ancrer dans le conteneur parent**.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque Windows Forms et sélectionnez **Propriétés**.

1. Dans la page **Propriétés**, sélectionnez l’onglet **Application**.

1. Dans la liste déroulante **Framework cible**, sélectionnez .NET Framework 4 (ou ultérieur).

1. La boîte de dialogue **Modification du Framework cible** s’affiche.

1. Cliquez sur **Oui**.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **références** et sélectionnez **Ajouter une référence**.

1. La boîte de dialogue **Ajouter une référence** s’affiche.

1. Choisissez l’onglet **.NET**, faites défiler la liste vers le bas, sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**, puis choisissez **OK**.

1. Si le **Concepteur de vues** n’est pas ouvert, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.cs**, puis sélectionnez **Concepteur de vues**.

1. Sur l’aire de conception, cliquez avec le bouton droit et sélectionnez **Afficher le code**.

1. (Facultatif) Remplacez le nom de la classe et le constructeur UserControl1 par un nom explicite, par exemple, MessageEditorControl :

    > [!NOTE]
    > L'exemple utilise MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. Ajoutez les propriétés suivantes pour obtenir et définir le texte dans RichTextBox1. L'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> utilise EditString et <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> utilise EditByteArray :

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Ajouter une classe au projet de bibliothèque de contrôles Windows Forms

Ajoutez une classe au projet. Elle sera utilisée pour implémenter les interfaces <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Vue d’ensemble du code dans cette procédure**

Le contrôle <xref:System.Windows.Forms.UserControl> de MessageEditorControl qui été créé dans la procédure précédente est instancié comme messageEditorControl :

```csharp
private MessageEditorControl messageEditorControl
```

L'instance messageEditorControl est hébergée dans la boîte de dialogue du plug-in créé par la méthode <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*>. En outre, <xref:System.Windows.Forms.RichTextBox> de messageEditorControl est rempli avec le contenu dans le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Toutefois, la création du plug-in ne peut pas se produire sauf si <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> retourne `true`. Dans le cas de cet éditeur, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> retourne `true` si le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> dans le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> contient « xml ».

Quand la modification du corps chaîne est effectuée et que l’utilisateur clique sur **OK** dans la boîte de dialogue du plug-in, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> est appelée pour obtenir le texte modifié sous forme de chaîne et mettre à jour le **Corps chaîne** dans la requête dans la demande de l’éditeur de tests de performances web.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Créer une classe et implémenter l’interface IStringHttpBodyEditorPlugin

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque de contrôles Windows Forms et sélectionnez **Ajouter un nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2. Sélectionnez **classe**.

3. Dans la zone de texte **Nom**, tapez un nom explicite pour la classe, par exemple `MessageEditorPlugins`.

4. Choisissez **Ajouter**.

   Class1 est ajouté au projet et est présenté dans l'éditeur de code.

5. Dans l’éditeur de code, ajoutez l’instruction `using` suivante :

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Collez le code suivant pour implémenter l’interface :

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Ajouter un IBinaryHttpBodyEditorPlugin à la classe

Implémentez l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Vue d’ensemble du code dans cette procédure**

L'implémentation de code de l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> est semblable au <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> comme décrit dans la section précédente. Toutefois, la version binaire utilise un tableau d'octets pour gérer les données binaires à la place d'une chaîne.

Le <xref:System.Windows.Forms.UserControl> de MessageEditorControl créé dans la première procédure est instancié comme messageEditorControl :

```csharp
private MessageEditorControl messageEditorControl
```

L'instance messageEditorControl est hébergée dans la boîte de dialogue du plug-in créé par la méthode <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*>. En outre, <xref:System.Windows.Forms.RichTextBox> de messageEditorControl est rempli avec le contenu dans le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Toutefois, la création du plug-in ne peut pas se produire sauf si <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> retourne `true`. Dans le cas de cet éditeur, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> retourne `true` si le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> dans le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> contient « msbin1 ».

Quand la modification du corps chaîne est effectuée et que l’utilisateur clique sur **OK** dans la boîte de dialogue du plug-in, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> est appelée pour obtenir le texte modifié sous forme de chaîne et mettre à jour **BinaryHttpBody.Data** dans la demande de l’éditeur de tests de performances web.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Pou ajouter le IBinaryHttpBodyEditorPlugin à la classe

- Créez ou copiez le code suivant sous la classe XmlMessageEditor ajoutée dans la procédure précédente pour instancier la classe Msbin1MessageEditor de l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> et implémenter les méthodes obligatoires :

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Générer et déployer les plug-ins

1. Dans le menu **générer** , choisissez **Générer \<Windows Form Control Library project name>**.

2. Fermez toutes les instances de Visual Studio.

   > [!NOTE]
   > Fermer Visual Studio permet de garantir que le fichier *.dll* n’est pas verrouillé avant d’essayer de le copier.

3. Copiez le fichier *. dll* résultant du dossier *bin\Debug* de votre projet (par exemple, *MessageEditors.dll*) dans *%ProgramFiles%\Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Ouvrez Visual Studio.

   Le fichier *.dll* est maintenant inscrit auprès de Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Vérifier les plug-ins avec un test de performances web

1. Créez un projet de test.

2. Créez un test de performances web et entrez l’URL d’un service web dans le navigateur.

3. Une fois l’enregistrement terminé, dans la éditeur de test de performances Web, développez la demande pour le service Web et sélectionnez un **corps de chaîne** ou un **corps binaire**.

4. Dans la fenêtre **Propriétés** , sélectionnez corps chaîne ou corps binaire, puis cliquez sur le bouton de sélection **(...)**.

   La boîte de dialogue **Modifier les données du corps HTTP** s’affiche.

5. Vous pouvez à présent modifier les données avant de cliquer sur **OK**. La méthode GetNewValue applicable est appelée pour mettre à jour le contenu dans le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Compiler le code

Vérifiez que le framework ciblé du projet de bibliothèque de contrôles Windows est .NET Framework 4.5. Par défaut, les projets de bibliothèque de contrôles Windows ciblent le framework .NET Framework 4.5 Client, qui ne permet pas d’inclure la référence Microsoft.VisualStudio.QualityTools.WebTestFramework.

Pour plus d’informations, consultez [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Créer un code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Comment : créer un plug-in de niveau demande](../test/how-to-create-a-request-level-plug-in.md)
- [Coder une règle d’extraction personnalisée pour un test de performances web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Coder une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)
- [Générer et exécuter un test de performances de site Web codé](../test/generate-and-run-a-coded-web-performance-test.md)
- [Comment : créer un complément Visual Studio pour la visionneuse de Résultats des tests performances de site Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
