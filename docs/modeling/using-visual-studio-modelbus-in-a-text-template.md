---
title: "Utilisation de Visual Studio ModelBus dans un mod&#232;le de texte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# Utilisation de Visual Studio ModelBus dans un mod&#232;le de texte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous écrivez des modèles de texte qui indiquent un modèle contenant des références de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, vous pouvez résoudre les références pour accéder aux modèles cibles.  Dans ce cas, vous devez adapter les modèles de texte et les langages référencés spécifique au domaine \(DSLs\) :  
  
-   Le domaine \(qui est la cible des références doit avoir un adaptateur ModelBus configuré pour l'accès des modèles de texte.  Si vous accédez également au langage DÉSOLÉ d'un autre code, l'adaptateur reconfiguré est requis en plus de l'adaptateur standard ModelBus.  
  
     le gestionnaire d'adaptateur doit hériter d' <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> et doit avoir l'attribut `[HostSpecific(HostName)]`.  
  
-   le modèle doit hériter d' <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Si vous souhaitez lire les modèles DÉSOLÉ qui ne contiennent pas de références ModelBus, vous pouvez utiliser les processeurs de directive qui sont générés dans vos projets DÉSOLÉ.  Pour plus d'informations, consultez [Accès aux modèles depuis des modèles de texte](../modeling/accessing-models-from-text-templates.md).  
  
 Pour plus d'informations sur les modèles de texte, consultez [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## Créer un adaptateur de modèle de bus pour l'accès des modèles de texte  
 Pour résoudre une référence ModelBus dans un modèle de texte, la cible DÉSOLÉ doit avoir un adaptateur compatible.  Les modèles de texte s'exécutent dans un AppDomain séparé des éditeurs de document de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] par conséquent, l'adaptateur doit charger le modèle plutôt que y accéder via DTE.  
  
#### Pour créer un adaptateur ModelBus compatible avec les modèles de texte  
  
1.  Si la solution de la cible DÉSOLÉ n'a pas de projet d' **ModelBusAdapter** , créez un à l'aide de l'Assistant d'extension Modelbus :  
  
    1.  Téléchargez et installez l'extension de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, si ce n'est déjà fait.  Pour plus d'informations, consultez [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Ouvrez le fichier de définition de langage spécifique à un domaine.  Cliquez avec le bouton droit sur l'aire de conception puis cliquez sur **Vérifiez Modelbus**.  
  
    3.  dans la boîte de dialogue, sélectionnez **Je souhaite exposer ce DÉSOLÉ au ModelBus**.  Vous pouvez sélectionner les deux options si vous souhaitez que ce DÉSOLÉ pour exposer ses modèles et pour consommer des références à d'autres langages spécifiques à un domaine.  
  
    4.  Cliquez sur **OK**.  Un nouveau projet « ModelBusAdapter » est ajouté à la solution DÉSOLÉ.  
  
    5.  cliquez sur **Transformer tous les modèles**.  
  
    6.  Régénérez la solution.  
  
2.  Si vous souhaitez accéder au langage DÉSOLÉ d'un modèle de texte et d'un autre code, tel que la commande, doublon le projet d' **ModelBusAdapter** :  
  
    1.  Dans l'Explorateur Windows, la copiez et collez le dossier qui contient **ModelBusAdapter.csproj**.  
  
    2.  renommez le fichier projet \(par exemple, à **T4ModelBusAdapter.csproj**\).  
  
    3.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de solution, pointez sur **Ajouter**, puis cliquez sur **Projet existant**.  Localisez le projet de l'adaptateur, **T4ModelBusAdapter.csproj**.  
  
    4.  Dans chaque fichier d' `*.tt` du projet, modifiez l'espace de noms.  
  
    5.  Cliquez avec le bouton droit sur le nouvel projet dans l'explorateur de solutions et cliquez sur les propriétés.  dans l'éditeur de propriétés, modifiez les noms de l'assembly généré et de l'espace de noms par défaut.  
  
    6.  Dans le projet de DslPackage, ajoutez une référence au projet d'adaptateur afin qu'il comporte des références aux deux cartes.  
  
    7.  Dans DslPackage \\ source.extension.tt, ajoutez une ligne qui référence le nouveau projet d'adaptateur.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Transformer tous les modèles** et permettent de générer la solution.  Aucune erreur de build ne se passe.  
  
3.  Dans le nouveau projet d'adaptateur, ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  dans AdapterManager.tt :  
  
    -   Modifiez la déclaration d'AdapterManagerBase afin qu'elle hérite d' <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   À la fin de le fichier, remplacez l'aide de l'attribut HostSpecific avant la classe d'AdapterManager.  supprimez la ligne suivante :  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         insérez la ligne suivante :  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Cet attribut filtre l'ensemble d'adaptateurs qui est disponible lorsqu'un consommateur modelbus recherche un adaptateur.  
  
5.  **Transformer tous les modèles** et permettent de générer la solution.  Aucune erreur de build ne se passe.  
  
## Écrivant un modèle de texte qui peut résoudre les références de ModelBus  
 En général, vous démarrez avec un modèle qui indique et génère des fichiers d'une « source » DÉSOLÉ.  Ce modèle utilise la directive générées dans le projet de la source DÉSOLÉ de lire source les fichiers de modèle de la façon décrite dans [Accès aux modèles depuis des modèles de texte](../modeling/accessing-models-from-text-templates.md).  Toutefois, la source DÉSOLÉ contient des références ModelBus à une « cible » DÉSOLÉ.  Vous voulez donc permettre au code du modèle pour résoudre les références et accéder à la cible DÉSOLÉ.  vous devez donc adapter le modèle en suivant ces étapes :  
  
-   Modifiez la classe de base d'un modèle à <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Incluez `hostspecific="true"` dans la directive de modèle.  
  
-   Ajoutez les références d'assembly à la cible DÉSOLÉ et son adaptateur, puis activez ModelBus.  
  
-   Vous n'avez pas besoin de la directive qui est générée dans le cadre de la cible DÉSOLÉ.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let’s assume they’re all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 Lorsque ce modèle de texte est exécuté, la directive d' `SourceDsl` charge le fichier `Sample.source`.  Le modèle peut accéder aux éléments de ce modèle, en commençant par `this.ModelRoot`.  Le code peut utiliser les classes de domaine et les propriétés de ce langage spécifique à un domaine.  
  
 En outre, le modèle peut résoudre les références de ModelBus.  Emplacement où le point de références au modèle cible, les directives d'assembly a laissé l'utilisation de code des classes de domaine et les propriétés du langage DÉSOLÉ de ce modèle.  
  
-   Si vous n'utilisez pas de directive générée par un projet DÉSOLÉ, vous devez également inclure le suivant.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Utilisez `this.ModelBus` pour obtenir l'accès au ModelBus.  
  
## Procédure pas \- à \- pas : Testez un modèle de texte qui utilise ModelBus  
 Dans cette procédure pas \- à \- pas, vous suivez ces étapes :  
  
1.  Élément deux langages spécifiques à un domaine.  Un langage spécifique à un domaine, *le consommateur*, a une propriété d' `ModelBusReference` qui peut faire référence à l'autre DÉSOLÉ, *le fournisseur*.  
  
2.  Créez deux adaptateurs ModelBus dans le fournisseur : un pour l'accès par les modèles de texte, l'autre pour le code ordinaire.  
  
3.  Créez des modèles d'instance du langages spécifiques à un domaine dans un projet expérimental unique.  
  
4.  définissez une propriété de domaine dans un modèle pour indiquer l'autre modèle.  
  
5.  Écrivez un gestionnaire de double\-clic qui ouvre le modèle vers lequel variable globale.  
  
6.  Écrivez un modèle de texte qui peut charger le premier modèle, suivez la référence à l'autre modèle, et lisent l'autre modèle.  
  
#### Construisez un DÉSOLÉ accessible à ModelBus  
  
1.  Créez une solution DÉSOLÉ.  Pour cet exemple, sélectionnez le modèle de solution de flux de travail.  définissez le nom de langue à `MBProvider` et l'extension de nom de fichier à « .provide ».  
  
2.  Dans le diagramme de définition DÉSOLÉ, cliquez avec le bouton droit dans une partie vide du diagramme qui n'est pas vers le haut, puis cliquez sur **Vérifiez Modelbus**.  
  
    -   Si vous ne voyez pas **Vérifiez Modelbus**, vous devez télécharger et installer l'extension VMSDK ModelBus.  Recherchez\-la sur le site VMSDK : [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  Dans la boîte de dialogue de **Vérifiez Modelbus** , sélectionnez **Exposez ce DÉSOLÉ au ModelBus**, puis cliquez sur **OK**.  
  
     un nouveau projet, `ModelBusAdapter`, est ajouté à la solution.  
  
 Vous avez maintenant un DÉSOLÉ accessible par les modèles de texte via ModelBus.  Des références à elle peut être résolu dans le code des commandes, des gestionnaires d'événements, ou des règles, qui s'exécutent dans l'AppDomain de l'éditeur de modèle de fichier.  Toutefois, le passage de modèles de texte dans un AppDomain séparé et ne peut pas accéder à un modèle lorsqu'il est modifié.  Si vous souhaitez accéder aux références ModelBus à ce langage DÉSOLÉ d'un modèle de texte, vous devez avoir un ModelBusAdapter séparé.  
  
#### Pour créer un adaptateur ModelBus configuré pour les modèles de texte  
  
1.  Dans l'Explorateur Windows, la copiez et collez le dossier qui contient ModelBusAdapter.csproj.  
  
     nommez le dossier T4ModelBusAdapter.  
  
     renommez le fichier projet T4ModelBusAdapter.csproj.  
  
2.  Dans l'explorateur de solutions, ajoutez T4ModelBusAdapter à la solution de MBProvider.  Cliquez avec le bouton droit sur le nœud de solution, pointez sur **Ajouter**, puis cliquez sur **Projet existant**.  
  
3.  Cliquez avec le bouton droit sur le nœud du projet de T4ModelBusAdapter puis cliquez sur propriétés.  Dans la fenêtre des propriétés du projet, modifiez **Nom de l'assembly** et **L'espace de noms par défaut** à `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  Dans chaque fichier de \*.tt dans T4ModelBusAdapter, insert « T4 » dans la dernière partie de l'espace de noms, afin que la ligne se présente comme suit.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  dans le projet d' `DslPackage` , ajoutez une référence de projet à `T4ModelBusAdapter`.  
  
6.  dans DslPackage \\ source.extension.tt, ajoutez la ligne suivante sous `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  dans le projet d' `T4ModelBusAdapter` , ajoutez une référence à : **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Ouvrez T4ModelBusAdapter \\AdapterManager application :  
  
    1.  modifiez la classe de base d'AdapterManagerBase à <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  Cette partie du fichier se présente maintenant comme suit.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  À la fin de le fichier, insérez l'attribut supplémentaire suivant devant la classe AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Le résultat obtenu ressemble au code ci\-dessous.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. cliquez sur **Transformer tous les modèles** dans la barre de titre de l'explorateur de solutions.  
  
10. Régénérez la solution.  Cliquez sur F5.  
  
11. Vérifiez que le DÉSOLÉ fonctionne en appuyant sur F5.  Dans le projet instance expérimentale de, ouvrez `Sample.provider`.  Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Les références ModelBus à ce langage DÉSOLÉ peuvent maintenant être résolues dans les modèles de texte ainsi que dans le code ordinaire.  
  
#### Construisez un DÉSOLÉ avec une propriété de domaine de référence ModelBus  
  
1.  Créez un nouveau domaine \(à l'aide de le modèle minimal de solution de langage.  nommez le langage MBConsumer et définissez l'extension de nom de fichier à « .consume ».  
  
2.  Dans le projet DÉSOLÉ, ajoutez une référence à l'assembly de MBProvider DÉSOLÉ.  Cliquez avec le bouton droit sur `MBConsumer\Dsl\References` puis cliquez sur **Ajouter une référence**.  Dans l'onglet de **Parcourir** , recherchez `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Cela vous permet de créer du code qui utilise l'autre DÉSOLÉ.  Si vous souhaitez créer des références à plusieurs langages spécifiques à un domaine, ajoutez \-les également.  
  
3.  Dans le diagramme de définition DÉSOLÉ, cliquez avec le bouton droit sur le diagramme puis cliquez sur **Vérifiez ModelBus**.  dans la boîte de dialogue, sélectionnez **Permettez à ce langage DÉSOLÉ pour consommer le ModelBus**.  
  
4.  Dans la classe `ExampleElement`, ajoutez une nouvelle propriété de domaine `MBR`, et dans la fenêtre Propriétés, affectez à son type à `ModelBusReference`.  
  
5.  Cliquez avec le bouton droit sur la propriété de domaine sur le diagramme puis cliquez sur **propriétés spécifiques de ModelBusReference de modification**.  dans la boîte de dialogue, sélectionnez **un élément de modèle**.  
  
     Définir le filtre de la boîte de dialogue Fichier au suivant.  
  
     `Provider File|*.provide`  
  
     La sous\-chaîne après « &#124; » est un filtre pour la boîte de dialogue de sélection de fichier.  Vous pouvez la définir pour autoriser tous les fichiers à l'aide de \*.\*  
  
     Dans la liste de **type d'élément de modèle** , entrez le nom d'une öre plus de classes de domaine dans le fournisseur DÉSOLÉ \(par exemple, Company.MBProvider.Task\).  ils peuvent être des classes abstraites.  Si vous laissez de liste, l'utilisateur peut définir référence à tout élément.  
  
6.  Fermez la boîte de dialogue et **Transformer tous les modèles**.  
  
 Vous avez créé un DÉSOLÉ qui peut contenir des références aux éléments dans un autre langage spécifique à un domaine.  
  
#### Créez une référence ModelBus à un autre fichier dans la solution  
  
1.  Dans la solution de MBConsumer, appuyez sur CTRL\+F5.  une instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] s'ouvre dans le projet d' **MBConsumer\\Debugging** .  
  
2.  ajoutez une copie de Sample.provide au projet d' **MBConsumer\\Debugging** .  Ceci est nécessaire parce qu'une référence ModelBus doit faire référence à un fichier dans la même solution.  
  
    1.  Cliquez avec le bouton droit sur le projet de débogage, pointez sur **Ajouter**, puis cliquez sur **Élément existant**.  
  
    2.  Dans la boîte de dialogue **Ajouter un élément** , définissez le filtre à **tous les fichiers \(\*.\*\)**.  
  
    3.  Naviguez jusqu'à `MBProvider\Debugging\Sample.provide` puis cliquez sur **Ajouter**.  
  
3.  Ouvrez `Sample.consume`.  
  
4.  Cliquez sur une forme d'exemple et, dans la fenêtre Propriétés, cliquez sur **\[...\]** dans la propriété de MBR.  dans la boîte de dialogue, cliquez sur **Parcourir** et sélectionnez `Sample.provide`.  Dans la fenêtre d'éléments, développez la tâche de type et sélectionnez l'un des éléments.  
  
5.  Enregistrez le fichier.  
  
     \(Ne fermez pas toujours l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].\)  
  
 Vous avez créé un modèle qui contient une référence ModelBus à un élément dans un autre modèle.  
  
#### Résoudre une référence ModelBus dans un modèle de texte  
  
1.  Dans l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez un fichier modèle de texte d'exemple.  définissez son contenu comme suit.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     Notez les points suivants :  
  
    1.  les attributs d' `hostSpecific` et d' `inherits` de la directive d' `template` doivent être définis.  
  
    2.  Le modèle du consommateur est accessible de la façon habituelle via le processeur de directive qui a été généré dans ce langage spécifique à un domaine.  
  
    3.  Les directives d'assembly et d'importation doivent pouvoir accéder au ModelBus de et aux types du fournisseur DÉSOLÉ.  
  
    4.  Si vous savez que de nombreux MBRs sont liés au même modèle, il est préférable d'appeler CreateAdapter une seule fois.  
  
2.  Vous enregistrez le modèle.  Vérifiez que le fichier texte obtenu ressemble au code ci\-dessous.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### Résoudre une référence ModelBus dans un gestionnaire de mouvements  
  
1.  Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], si elle s'exécute.  
  
2.  Ajoutez un fichier nommé MBConsumer \\Dsl\\Custom .cs et définissez son contenu comme suit.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Appuyez sur la combinaison de touches CTRL\+F5.  
  
4.  dans l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez `Debugging\Sample.consume`.  
  
5.  Forme double\-clic un.  
  
     si vous avez défini le MBR sur cet élément, le modèle référencé s'ouvre et l'élément référencé est sélectionné.  
  
## Voir aussi  
 [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)