---
title: 'Comment : utiliser des Assistants avec des modèles de projet'
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9d36ae9b3a4a4fbbb3c54cc3f3320e9878b6745
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905518"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Comment : utiliser des assistants avec des modèles de projet

Visual Studio fournit l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface qui, lorsqu’elle est implémentée, vous permet d’exécuter du code personnalisé lorsqu’un utilisateur crée un projet à partir d’un modèle.

La personnalisation du modèle de projet peut être utilisée pour afficher l’interface utilisateur personnalisée qui collecte les entrées d’utilisateur pour personnaliser le modèle, ajouter des fichiers supplémentaires au modèle ou toute autre action autorisée sur un projet.

Les <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> méthodes d’interface sont appelées à différents moments de la création du projet, à partir du moment où un utilisateur clique sur **OK** dans la boîte de dialogue **nouveau projet** . Chaque méthode de l’interface est nommée pour décrire le point auquel elle est appelée. Par exemple, Visual Studio appelle <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> immédiatement lorsqu’il commence à créer le projet, ce qui en fait un bon emplacement pour écrire du code personnalisé afin de collecter les entrées d’utilisateur.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Créer un projet de modèle de projet avec un projet VSIX

Vous commencez à créer un modèle personnalisé avec le projet de modèle de projet, qui fait partie du kit de développement logiciel (SDK) Visual Studio. Dans cette procédure, nous allons utiliser un projet de modèle de projet C#, mais il existe également un projet de modèle de projet Visual Basic. Ensuite, vous ajoutez un projet VSIX à la solution qui contient le projet de modèle de projet.

1. Créez un projet de modèle de projet C# (dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet** et recherchez « modèle de projet »). Nommez-le **MyProjectTemplate**.

   > [!NOTE]
   > Il se peut que vous soyez invité à installer le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

2. Ajoutez un nouveau projet VSIX dans la même solution que le projet de modèle de projet (dans **Explorateur de solutions**, sélectionnez le nœud de la solution, cliquez avec le bouton droit, puis sélectionnez **Ajouter**un  >  **nouveau projet** et recherchez « VSIX »). Nommez-le **MyProjectWizard.**

3. Définissez le projet VSIX comme projet de démarrage. Dans **Explorateur de solutions**, sélectionnez le nœud de projet VSIX, cliquez avec le bouton droit, puis sélectionnez **définir comme projet de démarrage**.

4. Ajoutez le projet de modèle en tant que ressource du projet VSIX. Dans **Explorateur de solutions**, sous le nœud de projet VSIX, recherchez le fichier *source. extension. vsixmanifest* . Double-cliquez dessus pour l’ouvrir dans l’éditeur de manifeste.

5. Dans l’éditeur de manifeste, sélectionnez l’onglet **ressources** sur le côté gauche de la fenêtre.

6. Dans l’onglet **ressources** , sélectionnez **nouveau**. Dans la fenêtre **Ajouter une nouvelle ressource** , pour le champ type, sélectionnez **Microsoft. VisualStudio. ProjectTemplate**. Dans le champ **source** , sélectionnez **un projet dans la solution actuelle**. Dans le champ **projet** , sélectionnez **MyProjectTemplate**. Cliquez ensuite sur **OK**.

7. Générez la solution et commencez le débogage. Une seconde instance de Visual Studio apparaît. (Cela peut prendre quelques minutes.)

8. Dans la deuxième instance de Visual Studio, essayez de créer un nouveau projet avec votre nouveau modèle (**fichier**  >  **nouveau**  >  **projet**, recherchez « MyProject »). Le nouveau projet doit apparaître avec une classe nommée **Class1**. Vous avez maintenant créé un modèle de projet personnalisé ! Arrêter le débogage maintenant.

## <a name="create-a-custom-template-wizard"></a>Assistant Création d’un modèle personnalisé

Cette procédure montre comment créer un Assistant personnalisé qui ouvre un Windows Form avant la création du projet. Le formulaire permet aux utilisateurs d’ajouter une valeur de paramètre personnalisée ajoutée au code source lors de la création du projet.

1. Configurez le projet VSIX pour lui permettre de créer un assembly.

2. Dans **Explorateur de solutions**, sélectionnez le nœud de projet VSIX. Vous devez voir la fenêtre **Propriétés** ci-dessous **Explorateur de solutions**. Si ce n’est pas le cas, sélectionnez **Afficher**la  >  **fenêtre des propriétés**ou appuyez sur **F4**. Dans la fenêtre **Propriétés** , sélectionnez les champs suivants pour `true` :

   - **Inclure l’assembly dans le conteneur VSIX**

   - **Inclure les symboles de débogage dans le conteneur VSIX**

   - **Inclure les symboles de débogage dans le déploiement VSIX local**

3. Ajoutez l’assembly en tant que ressource au projet VSIX. Ouvrez le fichier *source. extension. vsixmanifest* et sélectionnez l’onglet **ressources** . Dans la fenêtre **Ajouter une nouvelle ressource** , pour **type** , sélectionnez **Microsoft. VisualStudio. assembly**, pour **source** , sélectionnez **un projet dans la solution actuelle**et pour **projet** , sélectionnez **MyProjectWizard**.

4. Ajoutez les références suivantes au projet VSIX. (Dans **Explorateur de solutions**, sous le nœud de projet VSIX, sélectionnez **références**, cliquez avec le bouton droit, puis sélectionnez **Ajouter une référence**.) Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Framework** , recherchez l’assembly **System. Windows Forms** et sélectionnez-le. Recherchez et sélectionnez également les assemblys **System** et **System. Drawing** . Sélectionnez maintenant l’onglet **Extensions** . Recherchez l’assembly **EnvDTE** et sélectionnez-le. Recherchez également l’assembly **Microsoft. VisualStudio. TemplateWizardInterface** et sélectionnez-le. Cliquez sur **OK**.

5. Ajoutez une classe pour l’implémentation de l’Assistant au projet VSIX. (Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet VSIX, sélectionnez **Ajouter**, puis **nouvel élément**, puis **classe**.) Nommez la classe **WizardImplementation**.

6. Remplacez le code du fichier *WizardImplementationClass.cs* par le code suivant :

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    Le **UserInputForm** référencé dans ce code sera implémenté ultérieurement.

    La `WizardImplementation` classe contient des implémentations de méthode pour chaque membre de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . Dans cet exemple, seule la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode effectue une tâche. Toutes les autres méthodes ne font rien ou retournent `true` .

    La <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode accepte quatre paramètres :

   - <xref:System.Object>Paramètre qui peut être converti en objet racine pour <xref:EnvDTE._DTE> vous permettre de personnaliser le projet.

   - <xref:System.Collections.Generic.Dictionary%602>Paramètre qui contient une collection de tous les paramètres prédéfinis dans le modèle. Pour plus d’informations sur les paramètres de modèle, consultez [paramètres de modèle](../ide/template-parameters.md).

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>Paramètre qui contient des informations sur le type de modèle utilisé.

   - <xref:System.Object>Tableau qui contient un ensemble de paramètres passés à l’Assistant par Visual Studio.

     Cet exemple ajoute une valeur de paramètre à partir du formulaire d’entrée d’utilisateur au <xref:System.Collections.Generic.Dictionary%602> paramètre. Chaque instance du `$custommessage$` paramètre dans le projet est remplacée par le texte entré par l’utilisateur.

7. Créez maintenant le **UserInputForm**. Dans le fichier *WizardImplementation.cs* , ajoutez le code suivant après la fin de la `WizardImplementation` classe.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Le formulaire d’entrée utilisateur fournit un formulaire simple pour l’entrée d’un paramètre personnalisé. Le formulaire contient une zone de texte nommée `textBox1` et un bouton nommé `button1` . Lorsque l’utilisateur clique sur le bouton, le texte de la zone de texte est stocké dans le `customMessage` paramètre.

## <a name="connect-the-wizard-to-the-custom-template"></a>Connecter l’Assistant au modèle personnalisé

Pour que votre modèle de projet personnalisé utilise votre Assistant personnalisé, vous devez signer l’assembly de l’Assistant et ajouter des lignes à votre modèle de projet personnalisé pour qu’il sache où trouver l’implémentation de l’Assistant lors de la création d’un nouveau projet.

1. Signez l’assembly. Dans la **Explorateur de solutions**, sélectionnez le projet VSIX, cliquez avec le bouton droit, puis sélectionnez **Propriétés du projet**.

2. Dans la fenêtre **Propriétés du projet** , sélectionnez l’onglet **signature** . sous l’onglet **signature** , activez la case à cocher **signer l’assembly**. Dans le champ **choisir un fichier de clé de nom fort** , sélectionnez **\<New>** . Dans la fenêtre **créer une clé de nom fort** , dans le champ **nom de fichier de clé** , tapez **Key. snk**. Décochez le champ **protéger le fichier de clé par un mot de passe** .

3. Dans la **Explorateur de solutions**, sélectionnez le projet VSIX et recherchez la fenêtre **Propriétés** .

4. Affectez la **valeur true**au champ **copier la sortie de la génération dans le répertoire de sortie** . Cela permet à l’assembly d’être copié dans le répertoire de sortie lorsque la solution est reconstruite. Il est toujours contenu dans le `.vsix` fichier. Vous devez voir l’assembly afin de déterminer sa clé de signature.

5. Régénérez la solution.

6. Vous pouvez maintenant trouver le fichier Key. snk dans le répertoire du projet MyProjectWizard (* \<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*). Copiez le fichier *Key. snk* .

7. Accédez au répertoire de sortie et recherchez l’assembly (* \<your disk location> \ MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Collez le fichier *Key. snk* ici. (Cette opération n’est pas absolument nécessaire, mais elle facilitera les étapes suivantes.)

8. Ouvrez une fenêtre de commande et accédez au répertoire dans lequel l’assembly a été créé.

9. Recherchez l’outil de signature de *sn.exe* . Par exemple, sur un système d’exploitation Windows 10 64 bits, un chemin d’accès standard serait le suivant :

     *C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Si vous ne trouvez pas l’outil, essayez d’exécuter **où/r. sn.exe** dans la fenêtre de commande. Prenez note du chemin d’accès.

10. Extrayez la clé publique du fichier *Key. snk* . Dans la fenêtre commande, tapez

     **\<location of sn.exe>\sn.exe-p Key. snk-fichier. Key.**

     N’oubliez pas d’entourer le chemin d’accès de *sn.exe* par des guillemets s’il y a des espaces dans les noms de répertoire !

11. Récupérez le jeton de clé publique à partir du fichier journal :

     **\<location of sn.exe>\sn.exe-t fichier out. Key.**

     Encore une fois, n’oubliez pas les guillemets. Vous devez voir une ligne dans la sortie comme suit

     **Le jeton de clé publique est \<token>**

     Notez cette valeur.

12. Ajoutez la référence à l’Assistant personnalisé dans le fichier *. vstemplate* du modèle de projet. Dans le **Explorateur de solutions**, recherchez le fichier nommé *MyProjectTemplate. vstemplate*, puis ouvrez-le. Après la fin de la \<TemplateContent> section, ajoutez la section suivante :

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Où **MyProjectWizard** est le nom de l’assembly et **Token** est le jeton que vous avez copié à l’étape précédente.

13. Enregistrez tous les fichiers dans le projet et régénérez.

## <a name="add-the-custom-parameter-to-the-template"></a>Ajouter le paramètre personnalisé au modèle

Dans cet exemple, le projet utilisé comme modèle affiche le message spécifié dans le formulaire d’entrée d’utilisateur de l’Assistant personnalisé.

1. Dans le **Explorateur de solutions**, accédez au projet **MyProjectTemplate** et ouvrez *Class1.cs*.

2. Dans la `Main` méthode de l’application, ajoutez la ligne de code suivante.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Le paramètre `$custommessage$` est remplacé par le texte entré dans le formulaire d’entrée utilisateur lorsqu’un projet est créé à partir du modèle.

Voici le fichier de code complet avant qu’il ait été exporté dans un modèle.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Utiliser l’Assistant personnalisé

Vous pouvez maintenant créer un projet à partir de votre modèle et utiliser l’Assistant personnalisé.

1. Régénérez la solution et démarrez le débogage. Une seconde instance de Visual Studio doit apparaître.

2. Créez un nouveau projet MyProjectTemplate. (**Fichier**  >  **Nouveau**  >  **Projet**).

3. Dans la boîte de dialogue **nouveau projet** , recherchez « MyProject » pour rechercher votre modèle, tapez un nom, puis cliquez sur **OK**.

     Le formulaire d’entrée utilisateur de l’Assistant s’ouvre.

4. Tapez une valeur pour le paramètre personnalisé, puis cliquez sur le bouton.

     Le formulaire d’entrée utilisateur de l’Assistant se ferme et un projet est créé à partir du modèle.

5. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code source, puis cliquez sur **afficher le code**.

     Notez que `$custommessage$` a été remplacé par le texte entré dans le formulaire d’entrée utilisateur de l’Assistant.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personnaliser des modèles](../ide/customizing-project-and-item-templates.md)
- [WizardExtension, élément (modèles Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
