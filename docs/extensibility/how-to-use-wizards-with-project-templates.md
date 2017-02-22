---
title: "Comment&#160;: utiliser des Assistants avec des mod&#232;les de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IWizard (interface)"
  - "modèles de projet (Visual Studio), Assistants"
  - "modèles (Visual Studio), Assistants"
  - "modèles Visual Studio, Assistants"
  - "Assistants (Visual Studio), modèles de projet"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: utiliser des Assistants avec des mod&#232;les de projet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio fournit l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> qui, une fois implémentée, vous permet d'exécuter un code personnalisé lorsqu'un utilisateur crée un projet à partir d'un modèle.  
  
 La personnalisation du modèle de projet peut être utilisée pour effectuer les opérations suivantes :  
  
-   afficher une interface utilisateur personnalisée qui collecte les entrées d'utilisateur pour paramétrer le modèle ;  
  
-   ajouter des valeurs de paramètre à utiliser dans le modèle ;  
  
-   ajouter des fichiers supplémentaires au modèle ;  
  
-   exécuter pratiquement n'importe quelle action autorisée par le modèle objet Automation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sur un projet.  
  
 Les méthodes de l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> sont appelées à différents moments au fil de la création du projet, en commençant dès qu'un utilisateur clique sur **OK** dans la boîte de dialogue **Nouveau projet**.  Chaque méthode de l'interface est nommée pour décrire le moment auquel elle est appelée.  Par exemple, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] appelle immédiatement <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> dès qu'il commence à créer le projet, ce qui en fait un bon emplacement pour positionner un code personnalisé servant à collecter des entrées d'utilisateur.  
  
 Pour personnaliser le projet, la majeure partie du code que vous écrivez pour des Assistants personnalisés fait appel à l'objet <xref:EnvDTE.DTE>, qui constitue l'objet principal dans le modèle objet Automation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations sur le modèle objet Automation, consultez [Extension de l'environnement Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md) et [Guide de référence de l'extensibilité et de l'automation](../Topic/Automation%20and%20Extensibility%20Reference.md).  
  
## Création d'un Assistant de modèle personnalisé  
 Cette rubrique indique comment créer un Assistant personnalisé qui ouvre un Windows Form avant que le projet soit créé.  Ce formulaire permet à l'utilisateur d'ajouter une valeur de paramètre personnalisée qui sera à son tour ajoutée au code source pendant la création du projet.  Les étapes principales, expliquées individuellement en détails, sont les suivantes :  
  
#### Pour créer un Assistant de modèle personnalisé  
  
1.  Créez un assembly qui implémente l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
2.  Installez l'assembly dans le Global Assembly Cache.  
  
3.  Créez un projet et utilisez l'Assistant **Exportation de modèle** pour créer un modèle à partir du projet.  
  
4.  Modifiez le modèle en ajoutant un élément `WizardExtension` dans le fichier .vstemplate pour lier le modèle à l'assembly qui implémente <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
5.  Créer un projet à l'aide de l'Assistant personnalisé.  
  
## Implémentation d'IWizard  
 La première étape du processus consiste à créer un assembly qui implémente <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Cet assembly utilise la méthode <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> pour afficher un Windows Form qui permet à l'utilisateur d'ajouter une valeur de paramètre personnalisée, qui sera utilisée pendant la création du projet.  
  
> [!NOTE]
>  Cet exemple utilise [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pour implémenter <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, bien que vous puissiez également utiliser [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
#### Pour implémenter IWizard  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Consultez le code ci\-dessous pour un exemple [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d'une interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> intégralement implémentée.  
  
 Cet exemple contient deux fichiers de code : `IWizardImplementation`, une classe qui implémente l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, et `UserInputForm`, le Windows Form destiné aux entrées d'utilisateur.  
  
### Classe IWizardImplementation  
 La classe `IWizardImplementation` contient des implémentations de méthodes pour chaque membre de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Dans cet exemple, seule la méthode <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> réalise une tâche.  Les autres méthodes ne font rien ou retournent `true`.  
  
 La méthode <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> accepte quatre paramètres :  
  
-   Un paramètre <xref:System.Object>, dont un cast en objet <xref:EnvDTE._DTE> racine peut être effectué, pour vous permettre de personnaliser le projet.  
  
-   Un paramètre <xref:System.Collections.Generic.Dictionary%602> qui contient une collection de tous les paramètres prédéfinis dans le modèle.  Pour plus d'informations sur les paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
-   Un paramètre <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> qui contient des informations sur le type de modèle utilisé.  
  
-   Un tableau <xref:System.Object> qui contient un jeu de paramètres passé à l'Assistant par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Cet exemple ajoute une valeur de paramètre issue du formulaire des entrées d'utilisateur au paramètre <xref:System.Collections.Generic.Dictionary%602>.  Chaque instance du paramètre `$custommessage$` dans le projet est remplacée par le texte saisi par l'utilisateur.  Vous devez ajouter les assemblages suivants à votre projet :  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  L'UserInputForm utilisé dans cet exemple est défini dans la section suivante.  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
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
  
                customMessage = inputForm.get_CustomMessage();  
  
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
  
### Formulaire des entrées d'utilisateur  
 Le formulaire des entrées d'utilisateur constitue un support simple pour entrer un paramètre personnalisé.  Le formulaire contient une zone de texte nommée `textBox1` et un bouton nommé `button1`.  Lorsque le bouton est activé, le texte présent dans la zone de texte est enregistré dans le paramètre `customMessage`.  
  
##### Pour ajouter un Windows Form à la solution  
  
1.  Ajoutez le code suivant au fichier qui contient l'assistant d'implémentation.  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## Installation de l'assembly dans le Global Assembly Cache  
 L'assembly qui implémente <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> doit être signé avec un nom fort et installé dans le Global Assembly Cache.  
  
#### Pour installer l'assembly dans le Global Assembly Cache  
  
1.  Signez l'assembly avec un nom fort.  Pour plus d'informations, consultez [Comment : signer un assembly avec un nom fort](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md) ou [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/f468a7d3-234c-4353-924d-8e0ae5896564) ;  
  
2.  Installez l'assembly avec nom fort dans le Global Assembly Cache.  Pour plus d'informations, consultez [Comment : installer un assembly dans le Global Assembly Cache](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md).  
  
## Création d'un projet à utiliser comme modèle  
 Dans cet exemple, le projet utilisé en tant que modèle consiste en une application console qui affiche le message spécifié dans le formulaire des entrées d'utilisateur de l'Assistant personnalisé.  
  
#### Pour créer l'exemple de projet  
  
1.  Créez une application console [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
2.  Dans la méthode `Main` de l'application, ajoutez la ligne de code suivante :  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Le paramètre `$custommessage$` est remplacé par le texte saisi dans le formulaire des entrées d'utilisateur lorsqu'un projet est créé à partir du modèle.  
  
3.  Dans le menu **Fichier**, cliquez sur **Exporter le modèle**.  
  
4.  Dans l'Assistant **Exportation de modèle**, cliquez sur **Modèle de projet**, sélectionnez le projet approprié, puis cliquez sur **Suivant**.  
  
5.  Dans l'Assistant **Exportation de modèle**, entrez des informations descriptives relatives au modèle, activez la case à cocher **Importer automatiquement le modèle dans Visual Studio**, puis cliquez sur **Terminer**.  
  
     Le modèle s'affiche à présent dans la boîte de dialogue **Nouveau projet**, mais n'utilise pas l'Assistant personnalisé.  
  
 L'exemple suivant présente le fichier du code intégral avant son exportation vers un modèle.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## Modification du modèle  
 Maintenant que le modèle est créé et qu'il s'affiche dans la boîte de dialogue **Nouveau projet**, vous devez le modifier afin qu'il utilise l'assembly que vous avez créé au cours des étapes précédentes.  
  
#### Pour ajouter l'Assistant personnalisé au modèle  
  
1.  Localisez le fichier .zip qui contient le modèle.  
  
    1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
    2.  Cliquez sur **Projets et solutions**.  
  
    3.  Lisez le contenu de la zone de texte **Emplacement des modèles de projet pour l'utilisateur de Visual Studio**.  
  
     Par défaut, cet emplacement est Mes Documents\\Visual Studio *Version*\\Templates\\ProjectTemplates.  
  
2.  Extrayez le fichier .zip.  
  
3.  Ouvrez le fichier .vstemplate dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Après l'élément `TemplateContent`, ajoutez un élément [WizardExtension, élément \(modèles Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md) avec le nom fort de votre assembly d'Assistant personnalisé.  Pour plus d'informations sur la recherche du nom fort de votre assembly, consultez [Comment : visualiser le contenu du Global Assembly Cache](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md)et [Comment : référencer un assembly avec nom fort](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md).  
  
     L'exemple suivant présente un élément `WizardExtension`.  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## Utilisation de l'Assistant personnalisé  
 Vous pouvez à présent créer un projet à partir de votre modèle et utiliser l'Assistant personnalisé.  
  
#### Pour utiliser l'Assistant personnalisé  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, localisez votre modèle, tapez un nom et cliquez sur **OK**.  
  
     Le formulaire des entrées d'utilisateur de l'Assistant s'affiche.  
  
3.  Tapez une valeur pour le paramètre personnalisé, puis cliquez sur le bouton.  
  
     Le formulaire des entrées d'utilisateur de l'Assistant se ferme ; un projet est créé à partir du modèle.  
  
4.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier du code source, puis cliquez sur **Afficher le code**.  
  
     Remarquez que `$custommessage$` a été remplacé par le texte entré dans le formulaire des entrées d'utilisateur de l'Assistant.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension, élément \(modèles Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md)