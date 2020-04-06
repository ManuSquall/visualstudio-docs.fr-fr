---
title: 'Comment : utiliser des Assistants avec des modèles de projet'
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710547"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Comment: Utiliser des assistants avec des modèles de projet

Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> fournit l’interface qui, une fois mise en œuvre, vous permet d’exécuter du code personnalisé lorsqu’un utilisateur crée un projet à partir d’un modèle.

La personnalisation du modèle de projet peut être utilisée pour afficher l’interface utilisateur personnalisée qui recueille l’entrée de l’utilisateur pour personnaliser le modèle, ajouter des fichiers supplémentaires au modèle, ou toute autre action autorisée sur un projet.

Les <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> méthodes d’interface sont appelées à différents moments pendant la création du projet, à partir de dès qu’un utilisateur clique **SUR OK** sur la boîte de dialogue **New Project.** Chaque méthode de l’interface est nommée pour décrire le point auquel elle est appelée. Par exemple, Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Studio appelle immédiatement lorsqu’il commence à créer le projet, ce qui en fait un bon emplacement pour écrire du code personnalisé pour recueillir les entrées des utilisateurs.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Créer un projet de modèle de projet avec un projet VSIX

Vous commencez à créer un modèle personnalisé avec le projet de modèle de projet, qui fait partie du Studio visuel SDK. Dans cette procédure, nous utiliserons un projet de modèle de projet C, mais il existe également un projet de modèle de projet Visual Basic. Ensuite, vous ajoutez un projet VSIX à la solution qui contient le projet de modèle de projet.

1. Créez un projet de modèle de projet CMD (dans Visual Studio, sélectionnez **File** > **New** > **Project** et recherchez le « modèle de projet »). Nommez-le **MyProjectTemplate**.

   > [!NOTE]
   > On peut vous demander d’installer le Studio Visuel SDK. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Ajoutez un nouveau projet VSIX dans la même solution que le projet de modèle de projet (dans **Solution Explorer**, sélectionnez le nœud de solution, cliquez à droite, et **sélectionnez Ajouter** > **nouveau projet** et rechercher "vsix"). Nommez-le **MyProjectWizard.**

3. Définissez le projet VSIX comme le projet de démarrage. Dans **Solution Explorer**, sélectionnez le nœud du projet VSIX, cliquez à droite et **sélectionnez Set en tant que projet Startup**.

4. Ajoutez le projet de modèle comme un atout du projet VSIX. Dans **Solution Explorer**, sous le nœud du projet VSIX, trouvez le fichier *source.extension.vsixmanifest.* Double-cliquez dessus pour l’ouvrir dans l’éditeur manifeste.

5. Dans l’éditeur manifeste, sélectionnez l’onglet **Actifs** sur le côté gauche de la fenêtre.

6. Dans l’onglet **Actifs,** sélectionnez **Nouveau**. Dans la fenêtre **Add New Asset,** pour le champ Type, sélectionnez **Microsoft.VisualStudio.ProjectTemplate**. Dans le domaine **Source,** sélectionnez **un projet dans la solution actuelle.** Dans le domaine du **projet,** sélectionnez **MyProjectTemplate**. Cliquez ensuite sur **OK**.

7. Générez la solution et commencez le débogage. Une seconde instance de Visual Studio apparaît. (Cela peut prendre quelques minutes.)

8. Dans le second cas de Visual Studio, essayez de créer un nouveau projet avec votre nouveau modèle **(File** > **New** > **Project**, recherchez « myproject »). Le nouveau projet devrait apparaître avec une classe nommée **Class1**. Vous avez maintenant créé un modèle de projet personnalisé! Arrête de débogage maintenant.

## <a name="create-a-custom-template-wizard"></a>Créez un assistant modèle personnalisé

Cette procédure montre comment créer un assistant personnalisé qui ouvre un formulaire Windows avant la création du projet. Le formulaire permet aux utilisateurs d’ajouter une valeur de paramètre personnalisée ajoutée au code source lors de la création du projet.

1. Configurez le projet VSIX pour lui permettre de créer un assemblage.

2. Dans **Solution Explorer**, sélectionnez le nœud du projet VSIX. Ci-dessous **Solution Explorer**, vous devriez voir la fenêtre **Propriétés.** Si vous ne le faites pas, sélectionnez **View** > **Properties Window**, ou appuyez sur **F4**. Dans la fenêtre **Propriétés,** `true`sélectionnez les champs suivants pour :

   - **Inclure l’assemblage dans le conteneur VSIX**

   - **Inclure les symboles de déboille dans le conteneur VSIX**

   - **Inclure les symboles de déboque dans le déploiement local vsIX**

3. Ajoutez l’assemblage comme atout au projet VSIX. Ouvrez le fichier *source.extension.vsixmanifest* et sélectionnez l’onglet **Actifs.** Dans la fenêtre **Add New Asset,** pour **Type** select **Microsoft.VisualStudio.Assembly**, pour **Source** **sélectionnez un projet dans**la solution actuelle , et pour **Project** sélectionne **MyProjectWizard**.

4. Ajoutez les références suivantes au projet VSIX. (Dans **Solution Explorer**, sous le nœud du projet VSIX, sélectionnez **Références**, clic droit et **sélectionnez Ajouter la référence**.) Dans le dialogue **Add Reference,** dans l’onglet **Framework,** trouvez l’assemblage **system.Windows Forms** et sélectionnez-le. Trouvez et sélectionnez également les assemblages **System** et **System.Drawing.** Sélectionnez maintenant l’onglet **Extensions.** Trouvez l’assemblage **EnvDTE** et sélectionnez-le. Trouvez également l’assemblage **Microsoft.VisualStudio.TemplateWizardInterface** et sélectionnez-le. Cliquez sur **OK**.

5. Ajoutez une classe pour la mise en œuvre de l’assistant au projet VSIX. (Dans **Solution Explorer**, cliquez à droite sur le nœud de projet VSIX et sélectionnez **Ajouter**, puis **Nouvel article**, puis **Classe**.) Nommez la classe **WizardImplementation**.

6. Remplacer le code dans le fichier *WizardImplementationClass.cs* par le code suivant :

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

    **L’UserInputForm** référencé dans ce code sera implémenté ultérieurement.

    La `WizardImplementation` classe contient des implémentations de méthode pour chaque membre de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Dans cet exemple, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> seule la méthode effectue une tâche. Toutes les autres méthodes `true`ne font rien ou reviennent .

    La <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode accepte quatre paramètres :

   - Un <xref:System.Object> paramètre qui peut <xref:EnvDTE._DTE> être jeté à l’objet racine, pour vous permettre de personnaliser le projet.

   - Un <xref:System.Collections.Generic.Dictionary%602> paramètre qui contient une collection de tous les paramètres prédéfinis dans le modèle. Pour plus d’informations sur les paramètres du modèle, voir [paramètres Template](../ide/template-parameters.md).

   - Un <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> paramètre qui contient des informations sur le type de modèle utilisé.

   - Un <xref:System.Object> tableau qui contient un ensemble de paramètres transmis à l’assistant par Visual Studio.

     Cet exemple ajoute une valeur de paramètre du formulaire d’entrée de l’utilisateur au <xref:System.Collections.Generic.Dictionary%602> paramètre. Chaque instance `$custommessage$` du paramètre du projet sera remplacée par le texte saisi par l’utilisateur.

7. Maintenant, créez **l’UserInputForm**. Dans le *fichier WizardImplementation.cs,* ajoutez le code suivant `WizardImplementation` après la fin de la classe.

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

    Le formulaire d’entrée de l’utilisateur fournit un formulaire simple pour entrer un paramètre personnalisé. Le formulaire contient une `textBox1` boîte textuelle nommée et un bouton nommé `button1`. Lorsque le bouton est cliqué, le texte `customMessage` de la boîte de texte est stocké dans le paramètre.

## <a name="connect-the-wizard-to-the-custom-template"></a>Connectez l’assistant au modèle personnalisé

Afin que votre modèle de projet personnalisé pour utiliser votre assistant personnalisé, vous devez signer l’assemblage de l’assistant et ajouter quelques lignes à votre modèle de projet personnalisé pour lui faire savoir où trouver la mise en œuvre de l’assistant quand un nouveau projet est créé.

1. Signez l’assemblage. Dans le **Solution Explorer**, sélectionnez le projet VSIX, cliquez à droite et sélectionnez **les propriétés du projet**.

2. Dans la fenêtre **Propriétés du projet,** sélectionnez **l’onglet Signature.** dans **l’onglet Signature,** vérifiez **Signez l’assemblage**. Dans le **Choisissez un champ de fichiers clé de nom fort,** sélectionnez ** \<New>**. Dans la fenêtre **Créer une clé de nom fort,** dans le champ de nom de fichier **Key,** tapez **key.snk**. Décochez le **Protégez mon fichier clé avec un** champ de mot de passe.

3. Dans la **Solution Explorer**, sélectionnez le projet VSIX et trouvez la fenêtre **Propriétés.**

4. Définissez la sortie de construction de copie au champ **d’annuaire de sortie** **vrai.** Cela permet à l’assemblage d’être copié dans le répertoire de sortie lorsque la solution est reconstruite. Il est toujours `.vsix` contenu dans le fichier. Vous devez voir l’assemblée afin de connaître sa clé de signature.

5. Régénérez la solution.

6. Vous pouvez maintenant trouver le fichier key.snk dans l’annuaire du projet MyProjectWizard*\<(votre emplacement de disque>-MyProjectTemplate-MyProjectWizard.key.snk*). Copiez le fichier *key.snk.*

7. Rendez-vous à l’annuaire de sortie et trouvez*\<l’assemblage (votre emplacement de disque>-MyProjectTemplate/MyProjectWizard-bin-Debug-MyProjectWizard.dll*). Collez le fichier *key.snk* ici. (Ce n’est pas absolument nécessaire, mais il rendra les étapes suivantes plus facile.)

8. Ouvrez une fenêtre de commande et changez-vous à l’annuaire dans lequel l’assemblage a été créé.

9. Trouvez *l’outil de signature sn.exe.* Par exemple, sur un système d’exploitation Windows 10 64 bits, un chemin typique serait le suivant :

     *Fichiers de programme C : ''Microsoft SDKs’Windows’v10.0A’bin’NETFX 4.6.1 Outils*

     Si vous ne trouvez pas l’outil, essayez d’exécuter **où /R . sn.exe** dans la fenêtre de commande. Prenez note du chemin.

10. Extraire la clé publique du fichier *key.snk.* Dans la fenêtre de commande, tapez

     **\<emplacement de sn.exe>-sn.exe -p key.snk outfile.key.**

     N’oubliez pas d’entourer le chemin de *sn.exe* avec des guillemets s’il y a des espaces dans les noms d’annuaire !

11. Obtenez le jeton de clé publique de la fonction sortante:

     **\<emplacement de sn.exe>-sn.exe -t outfile.key.**

     Encore une fois, n’oubliez pas les guillemets. Vous devriez voir une ligne dans la sortie comme celle-ci

     **Le jeton \<de clé publique est symbolique>**

     Prenez note de cette valeur.

12. Ajoutez la référence à l’assistant personnalisé au fichier *.vstemplate* du modèle de projet. Dans la **Solution Explorer**, trouver le fichier nommé *MyProjectTemplate.vstemplate*, et l’ouvrir. Après la fin \<de la section TemplateContent>, ajoutez la section suivante :

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Où **MyProjectWizard** est le nom de l’assemblage, et **jeton** est le jeton que vous avez copié dans l’étape précédente.

13. Enregistrer tous les fichiers dans le projet et reconstruire.

## <a name="add-the-custom-parameter-to-the-template"></a>Ajouter le paramètre personnalisé au modèle

Dans cet exemple, le projet utilisé comme modèle affiche le message spécifié dans la forme d’entrée utilisateur de l’assistant personnalisé.

1. Dans la **Solution Explorer**, allez au projet **MyProjectTemplate** et ouvrez *Class1.cs*.

2. Dans `Main` la méthode de l’application, ajoutez la ligne de code suivante.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Le `$custommessage$` paramètre est remplacé par le texte entré dans le formulaire d’entrée de l’utilisateur lorsqu’un projet est créé à partir du modèle.

Voici le fichier de code complet avant qu’il n’ait été exporté vers un modèle.

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

## <a name="use-the-custom-wizard"></a>Utilisez l’assistant personnalisé

Maintenant, vous pouvez créer un projet à partir de votre modèle et utiliser l’assistant personnalisé.

1. Reconstruire la solution et commencer à débogage. Une seconde instance de Visual Studio doit apparaître.

2. Créez un nouveau projet MyProjectTemplate. (**Fichier** > **Nouveau** > **Projet**).

3. Dans la boîte de dialogue **du nouveau projet,** recherchez « mon projet » pour localiser votre modèle, tapez un nom et cliquez **sur OK**.

     Le formulaire d’entrée de l’utilisateur assistant s’ouvre.

4. Tapez une valeur pour le paramètre personnalisé et cliquez sur le bouton.

     Le formulaire d’entrée de l’utilisateur assistant se ferme, et un projet est créé à partir du modèle.

5. Dans **Solution Explorer**, cliquez à droite sur le fichier de code source et cliquez sur Code De **vue**.

     Avis `$custommessage$` qui a été remplacé par le texte entré dans le formulaire d’entrée de l’utilisateur assistant.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personnaliser des modèles](../ide/customizing-project-and-item-templates.md)
- [Élément WizardExtension (modèles Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
