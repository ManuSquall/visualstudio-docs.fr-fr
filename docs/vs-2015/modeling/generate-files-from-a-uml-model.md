---
title: Générer des fichiers à partir d’un modèle UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d58a8b98cb27527f3d4c464119fb5543f88e8ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182824"
---
# <a name="generate-files-from-a-uml-model"></a>Générer des fichiers à partir d'un modèle UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À partir d'un modèle UML, vous pouvez générer du code de programme, des schémas, des documents, des ressources et autres artefacts de tout genre. Une méthode commode permettant de générer des fichiers texte à partir d’un modèle UML consiste à utiliser [modèles de texte](../modeling/code-generation-and-t4-text-templates.md). Ces derniers vous permettent d'intégrer du code de programme dans le texte que vous souhaitez générer.  
  
 Il existe trois scénarios principaux :  
  
- [Génération de fichiers à partir d’une commande de menu](#Command) ou d’un mouvement. Vous définissez une commande [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui est disponible sur les modèles UML.  
  
- [Génération de fichiers à partir d’une application](#Application). Vous écrivez une application qui lit des modèles UML et génère des fichiers.  
  
- [Génération au moment du design](#Design). Vous utilisez un modèle pour définir certaines fonctionnalités de votre application et générer du code, des ressources, et ainsi de suite dans votre solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  Cette rubrique se termine par une discussion sur [comment utiliser la génération de texte](#What). Pour plus d’informations, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="Command"></a> Génération de fichiers à partir d’une commande de menu  
 Vous pouvez utiliser des modèles de texte de prétraitement dans une commande de menu UML. Dans le code du modèle de texte, ou dans une classe partielle distincte, vous pouvez lire le modèle illustré par le diagramme.  
  
 Pour plus d'informations sur ces fonctionnalités, consultez les rubriques suivantes :  
  
- [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Génération de texte à l’exécution à l’aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [Naviguer dans le modèle UML](../modeling/navigate-the-uml-model.md)  
  
  L'approche illustrée dans l'exemple suivant convient à la génération de texte à partir d'un modèle unique, quand vous initiez l'opération à partir de l'un des diagrammes de modèles. Pour traiter un modèle dans un contexte distinct, envisagez d’utiliser [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md) pour accéder au modèle et ses éléments.  
  
### <a name="example"></a>Exemples  
 Pour exécuter cet exemple, créez un projet d'Extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Le nom du projet qui est utilisé dans cet exemple est `VdmGenerator`. Dans le **source.extension.vsixmanifest** de fichiers, cliquez sur **ajouter du contenu** et définissez le champ de type sur **composant MEF** et chemin d’accès source référençant le projet actuel. Pour plus d’informations sur la configuration de ce type de projet, consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
 Ajoutez au projet un fichier C# qui contient le code suivant. Cette classe définit une commande de menu qui apparaîtra sur un diagramme de classes UML.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 Le fichier suivant est le modèle de texte. Il génère une ligne de texte pour chaque classe UML dans le modèle et une ligne pour chaque attribut dans chaque classe. Le code de lecture du modèle est incorporé dans le texte, délimité par `<# ... #>`.  
  
 Pour créer ce fichier, cliquez sur le projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Sélectionnez **modèle de texte prétraité**. Le nom de fichier pour cet exemple doit être **VdmGen.tt**. Le **un outil personnalisé** propriété du fichier doit être **TextTemplatingFilePreprocessor**. Pour plus d’informations sur les modèles de texte prétraités, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 Le modèle de texte génère une classe partielle C#, qui devient partie intégrante de votre projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dans un fichier distinct, ajoutez une autre déclaration partielle de la même classe. Ce code fournit au modèle l'accès au magasin de modèles UML :  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 Pour tester le projet, appuyez sur **F5**. Une nouvelle instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre. Dans cette instance, ouvrez ou créez un modèle UML qui contient un diagramme de classes. Ajoutez des classes au diagramme et des attributs à chaque classe. Avec le bouton droit dans le diagramme, puis cliquez sur l’exemple de commande `Generate VDM`. La commande crée le fichier `C:\Generated.txt`. Inspectez ce fichier. Son contenu doit ressembler au texte suivant, mais avec vos propres classes et attributs :  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
## <a name="Application"></a> Génération de fichiers à partir d’une Application  
 Vous pouvez générer des fichiers à partir d'une application qui lit un modèle UML. À cet effet, la méthode la plus flexible et fiable d’accès au modèle et ses éléments est [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Vous pouvez aussi utiliser l'API de base pour charger le modèle et le passer aux modèles de texte à l'aide des mêmes techniques que dans la section précédente. Pour plus d’informations sur le chargement d’un modèle, consultez [lire un modèle UML dans le code de programme](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="Design"></a> Génération de fichiers au moment du Design  
 Si votre projet comporte une méthode standard d'interprétation des données UML en tant que code, vous pouvez créer des modèles de texte qui vous permettent de générer du code dans votre projet à partir d'un modèle UML. En règle générale, vous auriez une solution qui contient le projet de modèle UML et un ou plusieurs projets pour le code d'application. Chaque projet de code pourrait contenir plusieurs modèles qui génèrent du code de programme, des ressources et des fichiers de configuration, en fonction du contenu du modèle. Le développeur peut exécuter tous les modèles en cliquant sur le **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions. Le code de programme est généralement généré sous la forme de classes partielles, pour faciliter l'intégration des parties écrites manuellement.  
  
 Vous pouvez distribuer un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de ce genre sous forme de modèle, pour que chaque membre de l'équipe puisse créer des projets qui génèrent du code à partir d'un modèle de la même façon. En règle générale, le modèle fait partie d'un package d'extension qui comprend des contraintes de validation sur le modèle pour s'assurer que les préconditions du code de génération sont remplies.  
  
### <a name="outline-procedure-for-generating-files"></a>Procédure de génération de fichiers  
  
- Pour ajouter un modèle à un projet, sélectionnez **modèle de texte** dans la boîte de dialogue Ajouter un nouveau fichier. Vous pouvez ajouter un modèle à la plupart des types de projets, mais pas aux projets de modélisation.  
  
- La propriété outil personnalisé du fichier de modèle doit être **TextTemplatingFileGenerator**, et l’extension de nom de fichier doit être .tt.  
  
- Le modèle doit avoir au moins une directive de sortie :  
  
     `<#@ output extension=".cs" #>`  
  
     Définissez le champ d'extension en fonction du langage de votre projet.  
  
- Pour permettre au code de génération dans votre modèle d'accéder au modèle, écrivez des directives `<#@ assembly #>` pour les assemblys nécessaires à la lecture d'un modèle UML. Utilisez `ModelingProject.LoadReadOnly()` pour ouvrir le modèle. Pour plus d’informations, consultez [lire un modèle UML dans le code de programme](../modeling/read-a-uml-model-in-program-code.md).  
  
- Le modèle est exécuté lorsque vous l’enregistrez et lorsque vous cliquez sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions.  
  
- Pour plus d’informations sur ce type de modèle, consultez [génération de Code au moment du Design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
- Dans un projet classique, vous aurez plusieurs modèles qui génèrent différents fichiers à partir du même modèle. La première partie de chaque modèle sera identique. Pour réduire cette duplication, déplacez les parties communes vers un fichier texte distinct, puis appelez-le à l'aide de la directive `<#@include file="common.txt"#>` dans chaque modèle.  
  
- Vous pouvez également définir un processeur de directive spécialisé qui vous permet de fournir des paramètres au processus de génération de texte. Pour plus d’informations, consultez [personnalisation de Transformation de texte T4](../modeling/customizing-t4-text-transformation.md).  
  
### <a name="example"></a>Exemple  
 Cet exemple génère une classe C# pour chaque classe UML dans le modèle source.  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Pour configurer une solution Visual Studio pour cet exemple  
  
1. Créez un diagramme de classes UML dans un projet de modélisation dans une nouvelle solution.  
  
   1. Dans le **Architecture** menu, cliquez sur **nouveau diagramme**.  
  
   2. Sélectionnez **diagramme de classes UML**.  
  
   3. Suivez les invites pour créer une solution et un projet de modélisation.  
  
   4. Ajoutez des classes au diagramme en faisant glisser l'outil Classe UML à partir de la boîte à outils.  
  
   5. Enregistrez le fichier.  
  
2. Créez un projet C# ou Visual Basic dans la même solution.  
  
   - Dans l’Explorateur de solutions, cliquez sur la solution, pointez sur **ajouter**, puis cliquez sur **nouveau projet**. Sous **modèles installés**, cliquez sur **Visual Basic** ou **Visual C#** , puis sélectionnez un type de projet comme **Application Console**.  
  
3. Ajoutez un fichier texte brut au projet Visual Basic ou C#. Ce fichier contiendra le code partagé si vous souhaitez écrire plusieurs modèles de texte.  
  
   - Dans l’Explorateur de solutions, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Sélectionnez **fichier texte**.  
  
     Insérez le texte affiché dans la section suivante.  
  
4. Ajoutez un fichier de modèle de texte au projet Visual Basic ou C#.  
  
   - Dans l’Explorateur de solutions, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Sélectionnez **modèle de texte**.  
  
     Insérez le code qui suit dans le fichier de modèle de texte.  
  
5. Enregistrez le fichier de modèle de texte.  
  
6. Examinez le code dans le fichier auxiliaire. Il doit contenir une classe pour chaque classe UML dans le modèle.  
  
   1. Dans un projet Visual Basic, cliquez sur **afficher tous les fichiers** dans la barre d’outils de l’Explorateur de solutions.  
  
   2. Développez le nœud du fichier de modèle dans l'Explorateur de solutions.  
  
#### <a name="content-of-the-shared-text-file"></a>Contenu du fichier texte partagé  
 Dans cet exemple, le fichier se nomme SharedTemplateCode.txt et il se trouve dans le même dossier que les modèles de texte.  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>Contenu du fichier de modèle de texte  
 Le texte suivant est placé dans le **.tt** fichier. Cet exemple génère des classes dans un fichier C# à partir des classes UML dans le modèle. Toutefois, vous pouvez générer des fichiers de n'importe quel type. Le langage du fichier généré n'est pas lié à celui dans lequel le code de modèle de texte est écrit.  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
## <a name="What"></a> Comment utiliser la génération de texte  
 La véritable puissance de la modélisation est obtenue quand vous utilisez des modèles pour la conception au niveau des impératifs ou de l'architecture. Vous pouvez utiliser des modèles de texte pour effectuer une partie de la conversion des idées de haut niveau en code. Dans de nombreux cas, cela n'aboutit pas à une correspondance de un à un entre les éléments des modèles UML et les classes ou autres parties du code de programme.  
  
 En outre, la transformation dépend de votre domaine qui pose problème ; il n'existe aucun mappage universel entre les modèles et le code.  
  
 Voici quelques exemples de génération de code à partir de modèles :  
  
- **Gammes de produits**. Fabrikam, Inc. crée et installe les bagages d’aéroport des systèmes de gestion. La plus grande partie du logiciel est très similaire d'une installation à l'autre, mais sa configuration dépend des mécanismes de manutention de bagages installés et de la façon dont ces éléments sont reliés par des tapis roulants. Au début d'un contrat, les analystes de Fabrikam discutent des impératifs avec la direction de l'aéroport et capturent le plan matériel à l'aide d'un diagramme d'activités UML. À partir de ce modèle, les membres de l'équipe de développement génèrent des fichiers de configuration, du code de programme, des plans et des documents utilisateur. Ils achèvent le travail par des ajouts manuels et des ajustements du code. À mesure qu'ils acquièrent de l'expérience d'un travail à l'autre, ils étendent la portée des éléments générés.  
  
- **Modèles**. Les développeurs de Contoso, Ltd créent souvent des sites web et conçoivent le schéma de navigation à l'aide de diagrammes de classes UML. Chaque page web est représentée par une classe et des associations représentent les liens de navigation. Les développeurs génèrent la plupart du code d'un site web à partir du modèle. Chaque page web correspond à plusieurs classes et entrées de fichiers de ressources.  Avec cette approche, la construction de chaque page est conforme à un modèle unique, ce qui la rend plus fiable et flexible que le code écrit manuellement. Le modèle est dans les modèles de génération, tandis que le modèle est utilisé pour capturer les aspects variables.  
  
- **Schémas**. Humongous Insurance possède des milliers de systèmes dans le monde entier. Ces systèmes utilisent différentes interfaces, langages et bases de données. L'équipe responsable de l'architecture centrale publie en interne des modèles de processus et de concepts d'entreprise. À partir de ces modèles, les équipes locales génèrent une partie de leurs schémas d'échange et de base de données, des déclarations dans le code de programme, et ainsi de suite. La présentation graphique des modèles aide les équipes à discuter des propositions. Les équipes créent plusieurs diagrammes qui montrent des sous-ensembles du modèle qui s'appliquent à différents domaines d'activité. Elles utilisent également la couleur pour mettre en évidence les zones susceptibles de changer.  
  
## <a name="important-techniques-for-generating-artifacts"></a>Techniques importantes pour générer des artefacts  
 Dans les exemples précédents, des modèles sont utilisés à diverses fins qui dépendent de l'entreprise, et l'interprétation des éléments de modélisation tels que les classes et les activités varie d'une application à l'autre. Les techniques suivantes sont utiles quand vous générez des artefacts à partir de modèles.  
  
- **Profils**. Dans un même domaine d'activité, l'interprétation d'un type d'élément peut varier. Par exemple, dans un diagramme de site web, certaines classes peuvent représenter des pages web et d'autres des blocs de contenu. Pour que ces distinctions soient plus claires du point de vue de l'utilisateur, vous pouvez définir des stéréotypes. Les stéréotypes vous permettent également de joindre des propriétés supplémentaires qui s'appliquent aux éléments de ce genre. Les stéréotypes sont empaquetés dans des profils. Pour plus d’informations, consultez [définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md).  
  
     Dans le code de modèle, il est facile d'accéder aux stéréotypes définis sur un objet. Par exemple :  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
- **Modèles contraints**. Les modèles que vous pouvez créer ne sont pas tous valides pour tout. Par exemple, dans les modèles de bagages d'aéroport de Fabrikam, il serait incorrect d'avoir un bureau d'enregistrement sans tapis roulant sortant. Vous pouvez définir des fonctions de validation qui aident les utilisateurs à respecter ces contraintes. Pour plus d’informations, consultez [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
- **Conserver les modifications manuelles**. Seule une partie des fichiers de solution peuvent être générés à partir d'un modèle. Dans la plupart des cas, vous devez pouvoir ajouter ou ajuster le contenu généré manuellement. Toutefois, il est important que ces modifications manuelles soient conservées quand la transformation de modèle est réexécutée.  
  
     Où vos modèles génèrent du code dans [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] langues, ils doivent générer des classes partielles afin que les développeurs peuvent ajouter des méthodes et du code. Il est également utile de générer chaque classe en tant que paire : une classe de base abstraite qui contient les méthodes et une classe héritière qui contient uniquement le constructeur. Cela permet aux développeurs de substituer les méthodes. Pour autoriser la substitution de l'initialisation, cette opération s'effectue dans une méthode distincte plutôt que dans les constructeurs.  
  
     Là où un modèle génère du code XML et autres types de sorties, il peut être plus difficile de séparer le contenu manuel du contenu généré. Une approche consiste à créer dans le processus de génération une tâche qui combine deux fichiers. Une autre approche consiste, pour les développeurs, à ajuster une copie locale du modèle de génération.  
  
- **Déplacer le code dans des assemblys distincts**. Nous vous déconseillons d'écrire des corps de code volumineux dans des modèles. Il est préférable de séparer le contenu généré et le calcul, et les modèles de texte ne sont pas bien pris en charge pour modifier le code.  
  
     Au lieu de cela, si vous devez effectuer des calculs substantiels pour générer du texte, construisez ces fonctions dans un assembly distinct et appelez ses méthodes à partir du modèle.
