---
title: Créer un éditeur de corps HTTP personnalisé pour l’éditeur de test de performances web dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0dc31bef7a7d2e91599cdc25be4f98445beda67f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896742"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Guide pratique pour créer un éditeur de corps HTTP personnalisé pour l’éditeur de test de performances web

Vous pouvez créer un éditeur de contenu personnalisé permettant de modifier le contenu du corps de type chaîne ou du corps binaire d’une demande de service web, de type SOAP, REST, asmx, wcf, RIA ou autre.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez implémenter ces types d'éditeurs :

-   **Éditeur de contenu de chaîne** Ceci est implémenté à l’aide de l’interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>.

-   **Éditeur de contenu binaire** Ceci est implémenté à l’aide de l’interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

Ces interfaces sont contenues dans l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

## <a name="create-a-windows-control-library-project"></a>Créer un projet de bibliothèque de contrôles Windows

### <a name="create-a-user-control-by-using-a-windows-control-library-project"></a>Créer un contrôle utilisateur moyen d'un projet Bibliothèque de contrôles Windows

1. Dans Visual Studio, dans le menu **Fichier**, choisissez **Nouveau**, puis sélectionnez **Projet**.

    La boîte de dialogue **Nouveau projet** s’affiche.

2. Sous **Modèles installés**, sélectionnez **Visual Basic** ou **Visual C#** en fonction de votre préférence de programmation, puis sélectionnez **Windows**.

   > [!NOTE]
   > Cet exemple utilise Visual C#.

3. Dans la liste des modèles, sélectionnez **Bibliothèque de contrôles Windows Forms**.

4. Dans la zone de texte **Nom**, tapez un nom, par exemple `MessageEditors`, puis choisissez **OK**.

   > [!NOTE]
   > Cet exemple utilise MessageEditors.

    Le projet est ajouté à la nouvelle solution et un <xref:System.Windows.Forms.UserControl> nommé *UserControl1.cs* est présenté dans le concepteur.

5. Dans la **Boîte à outils**, sous la catégorie **Contrôles communs**, faites glisser un <xref:System.Windows.Forms.RichTextBox> sur la surface de UserControl1.

6. Sélectionnez le glyphe de l’étiquette d’action (![Glyphe d’étiquette active](../test/media/vs_winformsmttagglyph.gif)) en haut à droite du contrôle <xref:System.Windows.Forms.RichTextBox>, puis sélectionnez **Ancrer dans le conteneur parent**.

7. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque Windows Forms et sélectionnez **Propriétés**.

8. Dans la page **Propriétés**, sélectionnez l’onglet **Application**.

9. Dans la liste déroulante **Framework cible**, sélectionnez **.NET Framework 4**.

10. La boîte de dialogue **Modification du Framework cible** s’affiche.

11. Cliquez sur **Oui**.

12. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis sélectionnez **Ajouter une référence**.

13. La boîte de dialogue **Ajouter une référence** s’affiche.

14. Choisissez l’onglet **.NET**, faites défiler la liste vers le bas, sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**, puis choisissez **OK**.

15. Si le **Concepteur de vues** n’est pas ouvert, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.cs**, puis sélectionnez **Concepteur de vues**.

16. Sur l’aire de conception, cliquez avec le bouton droit et sélectionnez **Afficher le code**.

17. (Facultatif) Remplacez le nom de la classe et le constructeur UserControl1 par un nom explicite, par exemple, MessageEditorControl :

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

18. Ajoutez les propriétés suivantes pour obtenir et définir le texte dans RichTextBox1. L'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> utilise EditString et <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> utilise EditByteArray :

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

### <a name="to-create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface-code"></a>Pour créer une classe et implémenter le code d'interface IStringHttpBodyEditorPlugin

1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque de contrôles Windows Forms et sélectionnez **Ajouter un nouvel élément**.

2.  La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

3.  Sélectionnez **Classe**.

4.  Dans la zone de texte **Nom**, tapez un nom explicite pour la classe, par exemple `MessageEditorPlugins`.

5.  Sélectionnez **Ajouter**.

     Class1 est ajouté au projet et est présenté dans l'éditeur de code.

6.  Dans l'éditeur de code, ajoutez l'instruction using suivant :

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

7.  Créez ou copiez le code suivant pour instancier la classe XmlMessageEditor de l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> et implémenter les méthodes obligatoires :

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
        /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
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

-   Créez ou copiez le code suivant sous la classe XmlMessageEditor ajoutée dans la procédure précédente pour instancier la classe Msbin1MessageEditor de l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> et implémenter les méthodes obligatoires :

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
            /// Create a UserControl to edit the specified bytes.  This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
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

### <a name="to-build-and-deploy-the-resulting-dll-for-the-istringhttpbodyeditorplugin-and-ibinaryhttpbodyeditorplugin"></a>Pour générer et déployer la DLL produite pour IStringHttpBodyEditorPlugin et IBinaryHttpBodyEditorPlugin

1.  Dans le menu **Générer**, choisissez **Générer \<nom du projet de bibliothèque de contrôles Windows Forms>**.

2.  Fermez toutes les instances de Visual Studio.

    > [!NOTE]
    > Fermer Visual Studio permet de garantir que le fichier *.dll* n’est pas verrouillé avant d’essayer de le copier.

3.  Copiez le fichier *.dll* résultant depuis le dossier *bin\debug* de vos projets (par exemple *MessageEditors.dll*) vers *%ProgramFiles%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4.  Ouvrez Visual Studio.

     Le fichier *.dll* est maintenant inscrit auprès de Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Vérifier les plug-ins avec un test de performances web

### <a name="to-test-your-plug-ins"></a>Pour tester vos plug-ins

1.  Créer un projet de test.

2.  Créez un test de performances web et entrez l’URL d’un service web dans le navigateur.

3.  Après l’enregistrement, développez la demande du service web dans l’éditeur de test de performances web et sélectionnez **Corps de type chaîne** ou **Corps binaire**.

4.  Dans la fenêtre Propriétés, sélectionnez Corps chaîne ou Corps binaire, puis le bouton de sélection **(…)**.

     La boîte de dialogue **Modifier les données du corps HTTP** s’affiche.

5.  Vous pouvez à présent modifier les données avant de cliquer sur **OK**. La méthode GetNewValue applicable est appelée pour mettre à jour le contenu dans le <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Compiler le code

Vérifiez que le framework ciblé du projet de bibliothèque de contrôles Windows est .NET Framework 4.5. Par défaut, les projets de bibliothèque de contrôles Windows ciblent le framework .NET Framework 4.5 Client, qui ne permet pas d’inclure la référence Microsoft.VisualStudio.QualityTools.WebTestFramework.

Pour plus d’informations, consultez [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Guide pratique pour créer un plug-in de niveau requête](../test/how-to-create-a-request-level-plug-in.md)
- [Coder une règle d’extraction personnalisée pour un test de performances web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Coder une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)
- [Guide pratique pour créer un complément Visual Studio pour l’afficheur de résultats de test de performances web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)