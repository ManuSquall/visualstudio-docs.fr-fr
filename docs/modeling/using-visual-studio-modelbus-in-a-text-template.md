---
title: "À l’aide de Visual Studio ModelBus dans un modèle de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: c496aaa7db6f2260764b413bfdf09f766be87384
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Utilisation de Visual Studio ModelBus dans un modèle de texte
Si vous écrivez des modèles de texte qui lisent un modèle qui contient [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus fait référence, vous pouvez résoudre les références pour accéder aux modèles de cible. Dans ce cas, vous devez adapter les modèles de texte et les langues de spécifique à un domaine (DSL) référencés :  
  
-   La DSL qui est la cible des références doit posséder une carte de ModelBus qui est configuré pour l’accès à partir de modèles de texte. Si vous accédez également la DSL depuis un autre code, la carte reconfigurée est requise en plus de l’adaptateur de ModelBus standard.  
  
     Le Gestionnaire d’adaptateur doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> et doit avoir l’attribut `[HostSpecific(HostName)]`.  
  
-   Le modèle doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Si vous souhaitez lire des modèles DSL qui ne contiennent pas de références ModelBus, vous pouvez utiliser les processeurs de directive sont générées dans les projets de votre DSL. Pour plus d’informations, consultez [l’accès à des modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md).  
  
 Pour plus d’informations sur les modèles de texte, consultez [génération du Code à l’aide de modèles de texte T4 au moment du Design](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Création d’un adaptateur de Bus pour l’accès à partir de modèles de texte  
 Pour résoudre une référence ModelBus dans un modèle de texte, la cible DSL doit avoir une carte compatible. Modèles de texte s’exécutent dans un AppDomain séparé à partir de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeurs de document, et par conséquent l’adaptateur doit charger le modèle au lieu d’y accéder via DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Pour créer un adaptateur de ModelBus est compatible avec les modèles de texte  
  
1.  Si la solution DSL cible n’a pas un **ModelBusAdapter** de projet, créez-en un à l’aide de l’Assistant Extension de Modelbus :  
  
    1.  Téléchargez et installez le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus Extension, si vous ne le n'avez pas déjà fait. Pour plus d’informations, consultez [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Ouvrez le fichier de définition DSL. Cliquez sur l’aire de conception, puis sur **activer un Modelbus**.  
  
    3.  Dans la boîte de dialogue, sélectionnez **souhaitée exposer ce DSL pour le ModelBus**. Vous pouvez sélectionner les deux options si vous souhaitez que cette DSL exposer ses modèles et d’utiliser des références aux autres DSL.  
  
    4.  Cliquez sur **OK**. Un nouveau projet « ModelBusAdapter » vient s'ajouter à la solution DSL.  
  
    5.  Cliquez sur **transformer tous les modèles**.  
  
    6.  Régénérez la solution.  
  
2.  Si vous souhaitez accéder du DSL à la fois à partir d’un modèle de texte et de tout autre code, telles que la commande, de dupliquer le **ModelBusAdapter** projet :  
  
    1.  Dans l’Explorateur Windows, copiez et collez le dossier qui contient **ModelBusAdapter.csproj**.  
  
    2.  Renommez le fichier de projet (par exemple, pour **T4ModelBusAdapter.csproj**).  
  
    3.  Dans **l’Explorateur de solutions**, cliquez sur le nœud solution, pointez sur **ajouter**, puis cliquez sur **projet existant**. Recherchez le nouveau projet d’adaptateur, **T4ModelBusAdapter.csproj**.  
  
    4.  Dans chaque `*.tt` fichier du nouveau projet, modifiez l’espace de noms.  
  
    5.  Cliquez sur le nouveau projet dans l’Explorateur de solutions, puis sur Propriétés. Dans l’éditeur de propriétés, modifiez les noms de l’assembly généré et l’espace de noms par défaut.  
  
    6.  Dans le projet DslPackage, ajoutez une référence vers le nouveau projet d’adaptateur afin qu’il possède des références aux deux cartes.  
  
    7.  Dans DslPackage\source.extension.tt, ajoutez une ligne qui fait référence à votre nouveau projet d’adaptateur.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Transformer tous les modèles** et régénérez la solution. Aucune erreur de build ne doit se produire.  
  
3.  Dans le nouveau projet d’adaptateur, ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  Dans AdapterManager.tt :  
  
    -   Modifiez la déclaration de AdapterManagerBase afin qu’elle hérite de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   À la fin du fichier, remplacez l’attribut HostSpecific avant de la classe AdapterManager. Supprimez la ligne suivante :  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Insérez la ligne suivante :  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Cet attribut filtre l’ensemble de cartes qui est disponible lorsqu’un consommateur modelbus recherche pour un adaptateur.  
  
5.  **Transformer tous les modèles** et régénérez la solution. Aucune erreur de build ne doit se produire.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Écriture d’un modèle de texte qui peut résoudre les références de ModelBus  
 En règle générale, vous commencez avec un modèle qui lit et génère des fichiers à partir d’une « source » DSL. Ce modèle utilise la directive est générée dans le projet DSL source pour lire les fichiers de modèle de source de la manière décrite dans [l’accès à des modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md). Toutefois, la source DSL contient des références de ModelBus à DSL « cible ». Par conséquent, vous souhaitez activer le modèle code résoudre les références et d’accéder à la cible DSL. Vous devez par conséquent adapter le modèle en suivant ces étapes :  
  
-   Modifiez la classe de base du modèle à <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Inclure `hostspecific="true"` dans la directive de modèle.  
  
-   Ajoutez les références d’assembly pour la cible DSL et de sa carte et permettre de ModelBus.  
  
-   Vous n’avez pas besoin de la directive est générée dans le cadre de la cible DSL.  
  
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
    // (Let's assume they're all in the same model file):  
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
  
 Lors de l’exécution de ce modèle de texte, le `SourceDsl` directive charge le fichier `Sample.source`. Le modèle peut accéder aux éléments de ce modèle, en commençant à partir de `this.ModelRoot`. Le code peut utiliser les classes de domaine et les propriétés de ce DSL.  
  
 En outre, le modèle peut résoudre les références ModelBus. Lorsque les références pointent vers le modèle cible, les directives d’assembly permettent le code d’utiliser les classes de domaine et les propriétés de DSL ce modèle.  
  
-   Si vous n’utilisez pas une directive qui est générée par un projet DSL, vous devez également inclure les éléments suivants.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Utilisez `this.ModelBus` pour obtenir l’accès à la ModelBus.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Procédure pas à pas : Test d’un modèle de texte qui utilise ModelBus  
 Dans cette procédure pas à pas, vous procédez comme suit :  
  
1.  Construire deux DSL. Un DSL, le *consommateur*, a une `ModelBusReference` propriété pouvant faire référence à l’autre DSL, le *fournisseur*.  
  
2.  Créez deux cartes ModelBus dans le fournisseur : un pour l’accès par des modèles de texte, l’autre pour du code ordinaire.  
  
3.  Créer des modèles de l’instance de la DSL dans un seul projet expérimental.  
  
4.  Définir une propriété de domaine dans un seul modèle pour pointer vers l’autre modèle.  
  
5.  Écrire un gestionnaire de double-clic qui ouvre le modèle qui est indiqué.  
  
6.  Écrire un modèle de texte qui peut charger le premier modèle, suivez la référence à l’autre modèle et lire l’autre modèle.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Construire une DSL est accessible à ModelBus  
  
1.  Créez une solution DSL. Dans cet exemple, sélectionnez le modèle de flux de tâches. Définissez le nom de la langue à `MBProvider` et l’extension de nom de fichier « .provide ».  
  
2.  Dans le schéma de définition DSL, cliquez sur une partie vide du diagramme qui n’est pas vers le haut, puis cliquez sur **activer un Modelbus**.  
  
    -   Si vous ne voyez pas **activer un Modelbus**, vous devez télécharger et installer l’extension VMSDK ModelBus. Rechercher sur le site VMSDK : [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  Dans le **activer un Modelbus** boîte de dialogue, sélectionnez **exposer cette DSL pour le ModelBus**, puis cliquez sur **OK**.  
  
     Un nouveau projet, `ModelBusAdapter`, est ajouté à la solution.  
  
 Vous avez maintenant une DSL est accessible par les modèles de texte via ModelBus. Références à ce dernier peuvent être résolus dans le code des commandes, des gestionnaires d’événements ou des règles, qui opèrent dans le domaine d’application de l’éditeur de fichier de modèle. Toutefois, les modèles de texte s’exécutent dans un AppDomain séparé et ne peut pas accéder à un modèle lorsqu’il est modifié. Si vous souhaitez accéder aux références ModelBus cette DSL à partir d’un modèle de texte, vous devez disposer d’un ModelBusAdapter distinct.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Pour créer un adaptateur de ModelBus est configuré pour les modèles de texte  
  
1.  Dans l’Explorateur Windows, copiez et collez le dossier qui contient ModelBusAdapter.csproj.  
  
     Nom du dossier T4ModelBusAdapter.  
  
     Renommez le fichier projet T4ModelBusAdapter.csproj.  
  
2.  Dans l’Explorateur de solutions, ajoutez T4ModelBusAdapter à la solution MBProvider. Cliquez sur le nœud solution, pointez sur **ajouter**, puis cliquez sur **projet existant**.  
  
3.  Cliquez sur le nœud du projet T4ModelBusAdapter, puis sur Propriétés. Dans la fenêtre Propriétés, modifiez la **nom de l’Assembly** et **par défaut de Namespace** à `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  Dans chaque fichier *.tt T4ModelBusAdapter, insérez « T4 » dans la dernière partie de l’espace de noms, afin que la ligne ressemble à ceci.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  Dans le `DslPackage` de projet, ajoutez une référence de projet à `T4ModelBusAdapter`.  
  
6.  Dans DslPackage\source.extension.tt, ajoutez la ligne suivante sous `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  Dans le `T4ModelBusAdapter` de projet, ajoutez une référence à : **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Ouvrez T4ModelBusAdapter\AdapterManager.tt :  
  
    1.  Modifiez la classe de base d'AdapterManagerBase en <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Cette partie du fichier ressemble maintenant à ceci.  
  
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
  
    2.  À la fin du fichier, insérez l’attribut supplémentaire suivant devant classe AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Le résultat ressemble à ceci.  
  
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
  
9. Cliquez sur **transformer tous les modèles** dans le titre de barre d’Explorateur de solutions.  
  
10. Régénérez la solution. Cliquez sur F5.  
  
11. Vérifiez que la DSL fonctionne en appuyant sur F5. Dans le projet expérimental, ouvrez `Sample.provider`. Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Références ModelBus cette DSL peuvent maintenant être résolus dans les modèles de texte et également dans du code ordinaire.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construire une DSL avec une propriété de domaine de ModelBus référence  
  
1.  Créer une nouveau DSL en utilisant le modèle de solution de langage minimale. Nommez le langage MBConsumer et l’extension de nom de fichier « .consume ».  
  
2.  Dans le projet DSL, ajoutez une référence à l’assembly MBProvider DSL. Avec le bouton droit `MBConsumer\Dsl\References` puis cliquez sur **ajouter une référence**. Dans le **Parcourir** onglet, recherchez`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Cela vous permet de vous permet de créer le code qui utilise l’autres DSL. Si vous souhaitez créer des références à plusieurs DSL, ajoutez-les également.  
  
3.  Dans le diagramme de définition DSL, cliquez sur le diagramme, puis **activer un ModelBus**. Dans la boîte de dialogue, sélectionnez **activer cette DSL consommer le ModelBus**.  
  
4.  Dans la classe `ExampleElement`, ajouter une nouvelle propriété de domaine `MBR`et dans la fenêtre Propriétés, définissez son type sur `ModelBusReference`.  
  
5.  Avec le bouton droit de la propriété de domaine sur le diagramme, puis cliquez sur **ModelBusReference de modifier les propriétés spécifiques**. Dans la boîte de dialogue, sélectionnez **un élément de modèle**.  
  
     Définir le filtre de la boîte de dialogue fichier à ce qui suit.  
  
     `Provider File|*.provide`  
  
     La sous-chaîne après « &#124; » est un filtre pour la boîte de dialogue de sélection de fichier. Vous pouvez définir pour permettre à tous les fichiers à l’aide de *.\*  
  
     Dans le **le type d’élément de modèle** liste, entrez les noms d’un ou plusieurs domaine classes dans le fournisseur DSL (par exemple, Company.MBProvider.Task). Ils peuvent être des classes abstraites. Si vous ne renseignez pas la liste, l’utilisateur peut définir la référence à un élément.  
  
6.  Fermez la boîte de dialogue et **transformer tous les modèles**.  
  
 Vous avez créé une DSL qui peut contenir des références à des éléments dans un autre DSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Créer une référence ModelBus à un autre fichier dans la solution  
  
1.  Dans la solution MBConsumer, appuyez sur CTRL + F5. Une instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] s’ouvre dans le **MBConsumer\Debugging** projet.  
  
2.  Ajouter une copie de Sample.provide à la **MBConsumer\Debugging** projet. Cela est nécessaire, car une référence ModelBus doit faire référence à un fichier dans la même solution.  
  
    1.  Cliquez sur le projet de débogage, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
    2.  Dans le **ajouter un élément** boîte de dialogue, définissez le filtre sur **tous les fichiers (\*.\*)** .  
  
    3.  Accédez à `MBProvider\Debugging\Sample.provide` puis cliquez sur **ajouter**.  
  
3.  Ouvrez `Sample.consume`.  
  
4.  Cliquez sur une forme d’exemple, dans la fenêtre Propriétés, cliquez sur **[...]**  dans la propriété MBR. Dans la boîte de dialogue, cliquez sur **Parcourir** et sélectionnez `Sample.provide`. Dans la fenêtre d’éléments, développer le type de tâche, puis sélectionnez un des éléments.  
  
5.  Enregistrez le fichier.  
  
     (Ne fermez pas encore l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 Vous avez créé un modèle qui contient une référence ModelBus à un élément dans un autre modèle.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Résoudre une ModelBus référence dans un modèle de texte  
  
1.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez un exemple de fichier de modèle de texte. Définissez son contenu comme suit.  
  
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
  
     Notez les points suivants :  
  
    1.  Le `hostSpecific` et `inherits` les attributs de la `template` directive doit être définie.  
  
    2.  Le modèle de consommateur est accessible via le processeur de directive qui a été généré dans ce DSL normalement.  
  
    3.  Les directives d’assembly et d’importation doivent être en mesure d’accéder ModelBus et les types du fournisseur DSL.  
  
    4.  Si vous savez que les nombreux MBR est liés au même modèle, il est préférable d’appeler CreateAdapter qu’une seule fois.  
  
2.  Enregistrez le modèle. Vérifiez que le fichier texte obtenu ressemble à ceci.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Résoudre une référence ModelBus dans un gestionnaire de mouvements  
  
1.  Fermez l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], si elle est en cours d’exécution.  
  
2.  Ajoutez un fichier nommé MBConsumer\Dsl\Custom.cs et définissez son contenu à la suivante.  
  
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
  
3.  Appuyez sur CTRL+F5.  
  
4.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez `Debugging\Sample.consume`.  
  
5.  Double-cliquez sur une forme.  
  
     Si vous avez défini le MBR sur cet élément, le modèle référencé s’ouvre et l’élément référencé est sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
