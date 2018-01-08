---
title: "Comment : utiliser des Assistants avec des modèles de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6e76a8880e488177f12cfb949ec46e95fd825986
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-use-wizards-with-project-templates"></a>Comment : utiliser des Assistants avec des modèles de projet
Visual Studio fournit la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface qui, lorsqu’elle est implémentée, vous permet d’exécuter du code personnalisé lorsqu’un utilisateur crée un projet à partir d’un modèle.  
  
 Personnalisation des modèles de projet peut servir à afficher l’interface utilisateur personnalisée qui collecte les entrées d’utilisateur pour personnaliser le modèle, ajouter des fichiers supplémentaires au modèle, ou toute autre action autorisée sur un projet.  
  
 Le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> méthodes d’interface sont appelées à différents moments pendant que le projet est en cours de création, dès qu’un utilisateur clique sur **OK** sur la **nouveau projet** boîte de dialogue. Chaque méthode de l’interface est nommée pour décrire le point auquel elle est appelée. Par exemple, Visual Studio appelle <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> immédiatement lorsqu’il démarre créer le projet, rendant un bon emplacement pour écrire du code personnalisé pour collecter les entrées d’utilisateur.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Création d’un projet de modèle de projet avec un projet VSIX  
 Commencer la création d’un modèle personnalisé avec le projet modèle projet., qui fait partie de Visual Studio SDK. Dans cette procédure, nous allons utiliser un projet de modèle de projet c#, mais il existe également un projet de modèle de projet Visual Basic. Puis vous ajoutez un projet VSIX à la solution qui contient le projet de modèle de projet.  
  
1.  Créer un projet de modèle de projet c# (dans Visual Studio, **fichier > Nouveau > projet > c# > extensibilité > modèle de projet c#**). Nommez-le **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Vous pouvez être invité à installer le Kit de développement logiciel Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Ajouter un nouveau projet VSIX (**fichier > Nouveau > projet > Visual c# > extensibilité > projet VSIX**) dans la même solution que le projet de modèle de projet (dans le **l’Explorateur de solutions**, sélectionnez le nœud de la solution, avec le bouton droit et sélectionnez **Ajouter > Nouveau projet**). Nommez-le **MyProjectWizard.**  
  
3.  Définissez le projet VSIX comme projet de démarrage. Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX, avec le bouton droit et sélectionnez **définir comme projet de démarrage**.  
  
4.  Ajouter le modèle de projet comme composant du projet VSIX. Dans le **l’Explorateur de solutions**, sous le nœud du projet VSIX, recherchez le **source.extension.vsixmanifest** fichier. Double-cliquez dessus pour l’ouvrir dans l’éditeur de manifeste.  
  
5.  Dans l’éditeur de manifeste, sélectionnez le **actifs** onglet sur le côté gauche de la fenêtre.  
  
6.  Dans le **actifs** onglet, sélectionnez **nouveau**. Dans le **ajouter un nouveau composant** fenêtre, pour le champ Type, sélectionnez **Microsoft.VisualStudio.ProjectTemplate**. Dans le **Source** champ, sélectionnez **un projet dans la solution actuelle**. Dans le **projet** champ, sélectionnez **MyProjectTemplate**. Cliquez ensuite sur **OK**.  
  
7.  Générez la solution et commencez le débogage. Une seconde instance de Visual Studio apparaît. (Cela peut prendre quelques minutes.)  
  
8.  Dans la deuxième instance de Visual Studio, essayez de créer un nouveau projet avec votre nouveau modèle. (**Fichier > Nouveau > projet > c# > MyProject modèle**). Le nouveau projet doit apparaître avec une classe nommée **Class1**. Vous venez de créer un modèle de projet personnalisé ! Arrêter le débogage maintenant.  
  
## <a name="creating-a-custom-template-wizard"></a>Création d’un Assistant de modèle personnalisé  
 Cette rubrique montre comment créer un Assistant personnalisé qui ouvre un Windows Form avant la création du projet. Le formulaire permet aux utilisateurs d’ajouter une valeur de paramètre personnalisé est ajoutée au code source pendant la création du projet.  
  
1.  Configurer le projet VSIX pour lui permettre de créer un assembly.  
  
2.  Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX. Sous l’Explorateur de solutions, vous devez voir le **propriétés** fenêtre. Si vous ne le faites pas, sélectionnez **vue > fenêtre Propriétés**, ou appuyez sur **F4**. Dans la fenêtre Propriétés, sélectionnez les champs suivants à `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Ajoutez l’assembly en tant qu’actif pour le projet VSIX. Ouvrez le fichier source.extension.vsixmanifest, puis sélectionnez le **actifs** onglet. Dans le **ajouter un nouveau composant** fenêtre, pour **Type** sélectionnez **Microsoft.VisualStudio.Assembly**, pour **Source** sélectionnez **A projet dans la solution actuelle**et pour **projet** sélectionnez **MyProjectWizard**.  
  
4.  Ajoutez les références suivantes au projet VSIX. (Dans le **l’Explorateur de solutions**, sous l’extension VSIX sélectionnez du nœud de projet **références**, avec le bouton droit, puis sélectionnez **ajouter une référence**.) Dans le **ajouter une référence** boîte de dialogue, dans le **Framework** onglet, recherchez la **System.Windows Forms** assembly et sélectionnez-le. Sélectionnez maintenant le **Extensions** rechercher de l’onglet le **EnvDTE** assembly et sélectionnez-le. Recherchez également le **Microsoft.VisualStudio.TemplateWizardInterface** assembly et sélectionnez-le. Cliquez sur **OK**.  
  
5.  Ajoutez une classe pour l’implémentation de l’Assistant pour le projet VSIX. (Dans l’Explorateur de solutions, cliquez sur le nœud du projet VSIX, puis sélectionnez **ajouter**, puis **un nouvel élément**, puis **classe**.) Nom de la classe **WizardImplementation**.  
  
6.  Remplacez le code dans le **WizardImplementationClass.cs** fichier avec le code suivant :  
  
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
  
     Le **UserInputForm** référencé dans ce code, vous définirez ultérieurement.  
  
     Le `WizardImplementation` contient des implémentations de méthode pour chaque membre de classe <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Dans cet exemple, uniquement les <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode effectue une tâche. Toutes les autres méthodes ne fait rien ou retournent `true`.  
  
     Le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode accepte quatre paramètres :  
  
    -   Un <xref:System.Object> paramètre qui peut être converti vers la racine <xref:EnvDTE._DTE> objet, pour vous permettre de personnaliser le projet.  
  
    -   A <xref:System.Collections.Generic.Dictionary%602> paramètre qui contient une collection de tous les paramètres prédéfinis dans le modèle. Pour plus d’informations sur les paramètres de modèle, consultez [les paramètres de modèle](../ide/template-parameters.md).  
  
    -   A <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> paramètre qui contient des informations sur le type de modèle est utilisé.  
  
    -   Un <xref:System.Object> tableau qui contient un jeu de paramètres passé à l’Assistant par Visual Studio.  
  
     Cet exemple ajoute une valeur de paramètre à partir du formulaire d’entrée utilisateur pour le <xref:System.Collections.Generic.Dictionary%602> paramètre. Chaque instance de la `$custommessage$` paramètre dans le projet sera remplacé par le texte entré par l’utilisateur. Vous devez ajouter les assemblys suivants à votre projet : **système** et **System.Drawing**.
  
7.  Créer maintenant les **UserInputForm**. Dans le **WizardImplementation.cs** , ajoutez le code suivant après la fin de la **WizardImplementation** classe.  
  
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
            }  
        }  
    ```  
  
     Le formulaire d’entrée utilisateur fournit une forme simple pour entrer un paramètre personnalisé. Le formulaire contient une zone de texte nommée `textBox1` et un bouton nommé `button1`. Lorsque le bouton est activé, le texte à partir de la zone de texte est stocké dans le `customMessage` paramètre.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>L’Assistant connexion pour le modèle personnalisé  
 Dans l’ordre pour votre modèle de projet personnalisé à utiliser votre Assistant personnalisé, vous devez signer l’assembly de l’Assistant et ajouter des lignes à votre modèle de projet personnalisé, il faut où trouver l’implémentation de l’Assistant Création d’un nouveau projet.  
  
1.  Signez l’assembly. Dans le **l’Explorateur de solutions**, sélectionnez le projet VSIX, avec le bouton droit et sélectionnez **propriétés du projet**.  
  
2.  Dans le **propriétés du projet** fenêtre, sélectionnez le **signature** onglet dans le **signature** onglet, vérifiez **signer l’assembly**. Dans le **choisir un fichier de clé de nom fort** champ, sélectionnez  **\<Nouveau >**. Dans le **créer une clé de nom fort** fenêtre, dans le **nom de fichier de clé** , tapez **key.snk**. Désactivez le **protéger mon fichier de clé avec un mot de passe** champ.  
  
3.  Dans le **l’Explorateur de solutions**, sélectionnez le projet VSIX et recherchez le **propriétés** fenêtre.  
  
4.  Définir le **répertoire de sortie à la sortie de génération de copie** au champ **true**. Ainsi, l’assembly doit être copié dans le répertoire de sortie lors de la reconstruction de la solution. Il est toujours contenue dans le fichier .vsix. Vous devez voir l’assembly afin de déterminer sa clé de signature.  
  
5.  Régénérez la solution.  
  
6.  Vous pouvez maintenant rechercher le fichier key.snk dans le répertoire du projet MyProjectWizard (**\<votre emplacement de disque > \MyProjectTemplate\MyProjectWizard\key.snk**). Copiez le fichier key.snk.  
  
7.  Accédez au répertoire de sortie et de trouver l’assembly (**\<votre emplacement de disque > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Collez le fichier key.snk ici. (Cela n’est pas absolument nécessaire, mais cela facilite les étapes suivantes).  
  
8.  Ouvrez une fenêtre de commande et accédez au répertoire dans lequel l’assembly a été créé.  
  
9. Rechercher les **sn.exe** outil de signature. Par exemple, sur un système d’exploitation de 64 bits de Windows 10, un chemin d’accès classique serait la suivante :  
  
     **Outils de \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 C:\Program (x86) de fichiers**  
  
     Si vous ne trouvez pas l’outil, essayez d’exécuter **où /R.  Sn.exe** dans la fenêtre de commande. Prenez note du chemin d’accès.  
  
10. Extraire la clé publique du fichier key.snk. Dans la fenêtre de commande, tapez  
  
     **\<emplacement de sn.exe > \sn.exe - p key.snk outfile.key.**  
  
     N’oubliez pas délimiter le chemin d’accès de sn.exe entre guillemets s’il existe des espaces dans les noms de répertoires.  
  
11. Obtenir la clé publique jeton dans le fichier de sortie :  
  
     **\<emplacement de sn.exe > \sn.exe - t outfile.key.**  
  
     Là encore, n’oubliez pas les guillemets. Vous devez voir une ligne dans la sortie comme suit  
  
     **Jeton de clé publique<token>**  
  
     Prenez note de cette valeur.  
  
12. Ajouter la référence à l’aide personnalisée pour le fichier .vstemplate du modèle de projet. Dans l’Explorateur de solutions, recherchez le fichier nommé MyProjectTemplate.vstemplate, puis ouvrez-le. Après la fin de la \<TemplateContent > section, ajoutez la section suivante :  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Où **MyProjectWizard** est le nom de l’assembly, et **jeton** est le jeton que vous avez copié à l’étape précédente.  
  
13. Enregistrer tous les fichiers du projet et régénérez.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Ajout du paramètre personnalisé au modèle  
 Dans cet exemple, le projet utilisé comme modèle affiche le message spécifié dans le formulaire d’entrée d’utilisateur de l’Assistant personnalisé.  
  
1.  Dans l’Explorateur de solutions, accédez à la **MyProjectTemplate** de projet et ouvrez **Class1.cs**.  
  
2.  Dans le `Main` (méthode) de l’application, ajoutez la ligne suivante de code.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Le paramètre `$custommessage$` est remplacé par le texte entré dans le formulaire d’entrée utilisateur lorsqu’un projet est créé à partir du modèle.  
  
 Voici le fichier de code complet avant qu’il a été exporté vers un modèle.  
  
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
  
## <a name="using-the-custom-wizard"></a>À l’aide de l’Assistant personnalisé  
 Vous pouvez maintenant créer un projet à partir de votre modèle et utiliser l’Assistant personnalisé.  
  
1.  Régénérez la solution et démarrer le débogage. Une seconde instance de Visual Studio doit apparaître.  
  
2.  Créer un nouveau projet MyProjectTemplate. (**Fichier > Nouveau > projet > c# > MyProjectTemplate**)  
  
3.  Dans le **nouveau projet** boîte de dialogue, localisez votre modèle, tapez un nom, puis cliquez sur **OK**.  
  
     Le formulaire d’entrée de l’utilisateur d’Assistant s’ouvre.  
  
4.  Tapez une valeur pour le paramètre personnalisé, puis cliquez sur le bouton.  
  
     Le formulaire d’entrée utilisateur l’Assistant se ferme et un projet est créé à partir du modèle.  
  
5.  Dans **l’Explorateur de solutions**, cliquez sur le fichier de code source, cliquez sur **afficher le Code**.  
  
     Notez que `$custommessage$` a été remplacé par le texte entré dans le formulaire d’entrée de l’utilisateur d’Assistant.  
  
## <a name="see-also"></a>Voir aussi  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)  
[Élément WizardExtension (modèles Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[Packages NuGet dans des modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
