---
title: "Proc&#233;dure pas &#224; pas&#160;: Publication d’un mod&#232;le de projet de contr&#244;le Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles, contrôles web"
  - "modèles de contrôles web"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Proc&#233;dure pas &#224; pas&#160;: Publication d’un mod&#232;le de projet de contr&#244;le Web
Vous pouvez créer un modèle de projet de contrôle web à utiliser comme base pour d’autres projets de contrôles web. Vous pouvez également distribuer le modèle comme extension VSIX.  
  
 Pour distribuer une extension VSIX, nous vous recommandons de l’ajouter au site web Galerie Visual Studio, car les développeurs peuvent utiliser le Gestionnaire d’extensions pour y rechercher des extensions nouvelles et mises à jour. Il est également possible de distribuer une extension en la plaçant sur un autre serveur, ou en la gravant sur un CD ou un autre support.  
  
 Cette procédure pas à pas explique comment créer un modèle de projet de contrôle web, puis comment le distribuer. La procédure pas à pas associée, intitulée [Procédure pas à pas : Publication d'une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md), explique comment créer et distribuer un contrôle web.  
  
 Cette procédure pas à pas contient les sections suivantes :  
  
-   Création d’un modèle de projet de contrôle web dans une extension VSIX  
  
-   Publication du modèle dans la galerie Visual Studio  
  
-   Installation du modèle à partir de la galerie Visual Studio  
  
-   Test du modèle installé  
  
-   Ajout d’un Assistant Action de débogage au modèle  
  
## Composants requis  
 Pour effectuer cette procédure pas à pas, vous devez comprendre ce que sont les contrôles web et savoir comment créer des projets, définir des propriétés de projet et utiliser l’instance expérimentale de Visual Studio. Visual Studio et le Kit de développement logiciel Visual Studio doivent être installés sur l’ordinateur. Avant de commencer cette procédure pas à pas, vous devez effectuer la [Procédure pas à pas : Publication d'une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Création d’un modèle de projet de contrôle web dans une extension VSIX  
 Pour créer un modèle de projet de contrôle web, créez d’abord un projet de contrôle web. Pour cette procédure pas à pas, commencez avec le projet de contrôle web ColorTextControl que vous avez créé dans [Procédure pas à pas : Publication d'une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
 Avant de publier un modèle de projet dans la galerie Visual Studio, utilisez l’Assistant **Export Template as VSIX** pour exporter le modèle comme extension VSIX et lui attribuer une icône pour vous aider à l’identifier dans le **Gestionnaire d’extensions** et une image pour illustrer ce qu’il fait.  
  
#### Pour préparer un projet de contrôle web pour la distribution  
  
1.  Dans Visual Studio, ouvrez le projet MyWebControls.  
  
2.  Utilisez le **Gestionnaire d’extensions** pour télécharger l’Assistant **Export Template Wizard** à partir du site web de la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329).  
  
     Après l’installation de l’Assistant, quand un projet est ouvert, **Export Template as VSIX** apparaît dans le menu **Fichier**.  
  
3.  Dans le menu **Fichier**, cliquez sur **Export Template as VSIX**.  
  
     ![Menu Fichier &#45; Exporter le projet en VSIX](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  Dans la page **Choose Template Type**, sélectionnez **Project Template**, puis MyWebControls.csproj. Cliquez sur **Next**.  
  
     ![Choisir un modèle de projet](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  Dans la page **Select Template Options**, sélectionnez `Extensibility Color Text Web Toolbox Control` comme **Template Name** et `Color text web control project that produces a VSIX extension.` comme **Template Description**.  
  
6.  En regard de la zone **Icon Image**, cliquez sur **Browse**. Dans la zone **File name** tapez `*.*`. Recherchez Color.bmp et cliquez sur **Open**.  
  
7.  En regard de la zone **Preview Image**, cliquez sur **Browse**. Dans la zone **File name** tapez `*.*`. Recherchez ScreenShot.bmp et cliquez sur **Open**. Cliquez sur **Next**.  
  
     ![Sélectionner les options de modèle](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  Dans la page **Select VSIX Options**, remplacez **Product Name** par `Extensibility Color Text Web Control Template`.  
  
9. Si vous le souhaitez, vous pouvez modifier les informations **Company Name**, **Version**, **License** et **Getting started guide URL**.  
  
10. Désactivez l’option **Automatically import the template into Visual Studio**. Cliquez sur **Finish**.  
  
     ![Désactiver l'importation automatique du modèle](../misc/media/pcwc_.png "PCWC\_")  
  
     Dans l’Explorateur Windows, dans le dossier ...\\My Documents\\Visual Studio *\<version\>*\\My Exported Templates\\, Extensibility Color Text Web Control Template.vsix est répertorié.  
  
## Publication du modèle dans la galerie Visual Studio  
 Le modèle de projet est maintenant prêt à être publié dans la galerie Visual Studio.  
  
#### Pour publier le modèle dans la galerie Visual Studio  
  
1.  Dans un navigateur web, ouvrez le site web de la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329).  
  
2.  Dans le coin supérieur droit, cliquez sur **sign in**.  
  
3.  Utilisez votre compte Microsoft pour vous connecter. Si vous n'avez pas de compte Microsoft, vous pouvez en créer un ici.  
  
4.  Cliquez sur **Upload**.  
  
5.  Dans **Step 1: Extension Type**, sélectionnez **Project or Item Template**, puis cliquez sur **Next**.  
  
6.  Dans **Step 2: Upload**, cliquez sur **Browse**. Dans le dossier \\My Exported Templates\\, sélectionnez Extensibility Color Text Web Control Template.vsix. Cliquez sur **Suivant**.  
  
7.  Dans **Step 3: Basic Information**, les informations de l’Assistant **Export Template as VSIX** sont affichées.  
  
8.  Affectez la valeur `ASP.NET` à **Category** et la valeur `toolbox, web control, templates` à **Tags**.  
  
9. Lisez et acceptez l’accord de collaboration puis, dans la zone, tapez le texte qui s’affiche.  
  
10. Cliquez sur **Create Contribution**, puis sur **Publish**.  
  
11. Recherchez Extensibility Color Text Web Control Template dans la galerie Visual Studio. Le nom du modèle doit figurer dans la liste.  
  
     ![La nouvelle liste de modèles de contrôle web](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## Installation du modèle à partir de la galerie Visual Studio  
 Maintenant que le modèle de projet de contrôle web est publié, installez\-le et testez\-le dans Visual Studio.  
  
#### Pour installer le modèle de projet de contrôle web dans Visual Studio  
  
1.  Dans Visual Studio, dans le menu **Outils**, cliquez sur **Gestionnaire d’extensions**.  
  
2.  Cliquez sur **Galerie en ligne**, puis recherchez Extensibility Color Text Web Control Template. Le nom du modèle doit figurer dans la liste.  
  
3.  Cliquez sur **Télécharger**. Une fois l’extension téléchargée, cliquez sur **Installer**.  
  
## Test du modèle installé  
 Vous pouvez maintenant utiliser le modèle de projet Extensibility Color Text Web Control pour créer des contrôles web personnalisés. Vous n’êtes pas obligé de créer chacun d’eux manuellement. Cette section montre comment utiliser le modèle pour créer un contrôle web BlueColorTextControl.  
  
#### Pour créer un contrôle web basé sur le modèle  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans le volet gauche, cliquez sur **Modèles en ligne**, développez **Modèles**, puis cliquez sur **ASP.NET**. Dans le volet central, cliquez sur **Extensibility Color Text Web Control Template**.  
  
     ![Sélectionner le modèle web du texte de couleur d'extensibilité](../misc/media/pcwc_newprojecttemplate.png "PCWC\_NewProjectTemplate")  
  
3.  Affectez `MoreWebControls` comme **Nom**. Cliquez sur **OK**.  
  
4.  Dans l’**Explorateur de solutions**, renommez ColorTextControl.cs en BlueColorTextControl.cs.  
  
5.  Double\-cliquez sur BlueColorTextControl.cs pour l’ouvrir dans l’éditeur.  
  
6.  Dans l’attribut `ToolboxData`, remplacez les deux occurrences de `ColorTextControl` par `BlueColorTextControl`.  
  
     Ces valeurs spécifient les balises d’ouverture et de fermeture qui sont générées pour le contrôle quand vous le faites glisser de la **Boîte à outils** vers une page web au moment du design.  Elles doivent correspondre au nom de la classe de contrôle, qui est également le nom du contrôle qui apparaît dans la **Boîte à outils**.  
  
     Le début du code source de la classe de contrôle doit maintenant ressembler au code suivant.  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  Dans la méthode `get`, remplacez `color:green` par `color:blue`.  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     Le texte est encapsulé dans une balise span qui le colore en bleu.  
  
8.  Générez le projet MoreWebControls.  
  
## Test du nouveau contrôle web  
 Vous pouvez maintenant tester si le nouveau contrôle web est disponible dans la **Boîte à outils**. Toutefois, bien que le projet MoreWebControls soit ouvert, une pression sur la touche F5 ne démarre pas d’instance expérimentale de Visual Studio permettant de tester le contrôle. Cela est dû au fait que le projet est basé sur le modèle Extensibility Color Text Web Control Template, qui ne peut pas encore définir d’action de débogage. \(La section suivante montre comment ajouter au modèle un Assistant qui définit l’action de débogage.\) Pour l’instant, pour tester le contrôle, procédez comme suit.  
  
#### Pour tester le nouveau contrôle web  
  
1.  Pour ouvrir une instance expérimentale de Visual Studio, démarrez l’instance expérimentale.  
  
    1.  Dans [!INCLUDE[win7](../debugger/includes/win7_md.md)], utilisez le menu **Démarrer** \(**Démarrer\/Tous les programmes\/Kit de développement logiciel SDK Microsoft Visual Studio \<version\>\/Outils\/Démarrer une instance expérimentale de Microsoft Visual Studio \<version\>**.  
  
    2.  Dans [!INCLUDE[win81](../debugger/includes/win81_md.md)], dans l’écran d’**accueil**, tapez **Démarrer une instance expérimentale de Microsoft Visual Studio \<version\>**.  
  
2.  Créez un projet d’application web.  
  
3.  Dans le projet, ouvrez default.aspx. Vérifiez que l’affichage **Source** est visible.  
  
4.  Dans la **Boîte à outils**, dans la catégorie **MoreWebControls**, **BlueColorTextControl** doit être affiché.  
  
     ![MoreWebControls BlueColorTextControl](../misc/media/pcwc_toolbox2.png "PCWC\_Toolbox2")  
  
5.  Faites glisser un BlueColorTextControl quelque part dans la balise `body` de la page web.  
  
6.  Dans la balise `ColorTextControl`, ajoutez un attribut `Text` et affectez\-lui la valeur `Think Blue!`. La balise doit ressembler à celle qui suit.  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  Appuyez sur F5 pour démarrer le serveur de développement ASP.NET.  
  
     L’affichage de BlueColorTextControl doit ressembler à l’image suivante.  
  
     ![BlueColorTextControl restitue Think Blue](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  Fermez le serveur de développement ASP.NET.  
  
9. Fermez l’instance expérimentale de Visual Studio.  
  
## Ajout d’un Assistant Action de débogage au modèle  
 Comme indiqué dans la section précédente, si vous appuyez sur F5 quand le projet MoreWebControls est ouvert, aucune instance expérimentale de Visual Studio n’est ouverte. Au lieu de cela, le message suivant s’affiche : « Un projet avec un type de sortie de bibliothèque de classes ne peut pas être démarré directement ». Cela se produit quand un projet ne connaît pas l’emplacement de l’instance expérimentale. Toutefois, vous pouvez permettre à un modèle de déterminer l’emplacement de l’instance expérimentale sur un ordinateur cible et de définir l’action de débogage. Après cela, tous les projets sur l’ordinateur qui sont basés sur ce modèle répondront à une pression sur la touche F5 comme prévu.  
  
 Chaque modèle de projet d’extensibilité inclus dans le Kit de développement logiciel Visual Studio contient un Assistant qui s’exécute pendant l’installation, recherche l’instance expérimentale sur l’ordinateur cible et définit l’action de débogage. Vous pouvez créer votre propre Assistant pour effectuer ces opérations, et vous pouvez l’inclure dans chaque modèle que vous distribuez.  
  
 Pour ajouter un Assistant Action de débogage au modèle Extensibility Color Text Web Control Template, vous devez supprimer la première version du modèle, y ajouter l’Assistant, puis la recréer.  
  
#### Pour supprimer la première version du modèle  
  
1.  Sur le site web de la galerie Visual Studio, dans le coin supérieur gauche, cliquez sur **My Contributions**. Le nom **Extensibility Color Text Web Control Template** s’affiche.  
  
2.  Pour supprimer définitivement votre modèle de projet de la galerie Visual Studio, cliquez sur **Delete**.  
  
3.  Dans Visual Studio, dans le menu **Outils**, cliquez sur **Gestionnaire d’extensions**.  
  
4.  Sélectionnez **Extensibility Color Text Web Control Template**, puis cliquez sur **Désinstaller**.  
  
5.  Fermez le **Gestionnaire d’extensions**.  
  
6.  Fermez la solution MoreWebControls.  
  
7.  Fermez Visual Studio.  
  
8.  Supprimez le dossier de solution MoreWebControls.  
  
9. Pour terminer le processus de désinstallation, redémarrez Visual Studio.  
  
 L’Assistant Action de débogage doit avoir une implémentation publique de `Microsoft.VisualStudio.TemplateWizard.IWizard` et doit être signé à l’aide d’un nom fort d’assembly.  
  
#### Pour créer l’Assistant Action de débogage  
  
1.  Dans la boîte de dialogue **Nouveau projet**, créez un projet **Visual C\#**, **Windows**, **Bibliothèque de classes** et nommez\-le `MyWizard`.  
  
2.  Dans le nouveau projet, renommez class1.cs en MyWizard.cs.  
  
3.  Remplacez le contenu de MyWizard.cs par le code suivant.  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  Ajoutez les références suivantes au projet. Si plusieurs choix sont disponibles, sélectionnez la référence qui a un chemin vers [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  Cliquez avec le bouton droit sur le projet MyWizard, puis cliquez sur **Propriétés**. Sous l’onglet **Signature**, sélectionnez l’option **Signer l’assembly**.  
  
6.  Dans la liste **Choisir un fichier de clé de nom fort**, sélectionnez **\<Nouveau...\>**. La boîte de dialogue **Créer une clé de nom fort** s’affiche.  
  
7.  Affectez la valeur `key.snk` à **Nom du fichier de clé** et désactivez l’option **Protéger mon fichier de clé par un mot de passe**.  
  
     ![Spécifier un fichier clé](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  Cliquez sur **OK** pour ajouter key.snk au projet.  
  
9. Générez le projet MyWizard comme version Release. L’Assistant est maintenant disponible.  
  
10. Fermez la solution MyWizard.  
  
#### Pour incorporer l’Assistant et recréer le modèle  
  
1.  Suivez les étapes décrites dans la section précédente, Création d’un modèle de projet de contrôle web dans une extension VSIX, mais effectuez ces modifications et ajouts :  
  
    -   Vous n’êtes pas obligé de retélécharger l’Assistant **Export Template as VSIX**.  
  
    -   Dans l’Assistant **Export Template as VSIX**, dans la page **Select VSIX Options**, dans la zone **Wizard**, recherchez le fichier \\bin\\Release\\MyWizard.dll que vous avez créé lors des étapes précédentes et sélectionnez\-le.  
  
         ![Spécifier l'assembly de l'assistant](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   Lorsque vous êtes invité à remplacer le fichier de sortie d’extension VSIX existant, cliquez sur **Yes**.  
  
2.  Lorsque vous atteignez la section Testing the New Web Control, appuyez sur F5. Une instance expérimentale de Visual Studio doit démarrer.  
  
## Étapes suivantes  
 Cette procédure pas à pas vous a montré comment utiliser l’Assistant **Export Template as VSIX** pour créer et distribuer un modèle de projet. Si vous souhaitez contrôler davantage le modèle de projet, par exemple choisir l’icône affichée dans la boîte de dialogue **Nouveau projet**, vous devez créer explicitement le modèle de projet et l’envelopper dans une extension VSIX. Pour plus d’informations, consultez [Creating and Sharing Project & Item Templates](http://go.microsoft.com/fwlink/?LinkId=194551) sur le site web du Blog Visual Studio.  
  
## Voir aussi  
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)