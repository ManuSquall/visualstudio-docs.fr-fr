---
title: Utilisation de ModelBus dans un modèle de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0d18103d2990b2734e4db1d1e7dc4261e08e7a7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301371"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Utilisation de Visual Studio ModelBus dans un modèle de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous écrivez des modèles de texte qui lisent un modèle qui contient [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] références ModelBus, vous souhaiterez peut-être résoudre les références pour accéder aux modèles cibles. Dans ce cas, vous devez adapter les modèles de texte et les langages spécifiques à un domaine référencés (DSL) :

- La solution DSL qui est la cible des références doit avoir un adaptateur ModelBus configuré pour l’accès à partir de modèles de texte. Si vous accédez également à la solution DSL à partir de tout autre code, la carte reconfigurée est nécessaire en plus de l’adaptateur ModelBus standard.

     Le gestionnaire d’adaptateur doit hériter de [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) et doit avoir l’attribut `[HostSpecific(HostName)]`.

- Le modèle doit hériter de [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Si vous souhaitez lire des modèles DSL qui ne contiennent pas de références ModelBus, vous pouvez utiliser les processeurs de directive qui sont générés dans vos projets DSL. Pour plus d’informations, consultez [accès aux modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md).

 Pour plus d’informations sur les modèles de texte, consultez [génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Création d’un adaptateur de Bus de modèle pour l’accès à partir de modèles de texte
 Pour résoudre une référence ModelBus dans un modèle de texte, DSL cible doit avoir une carte compatible. Les modèles de texte s’exécutent dans un AppDomain distinct du [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeurs de documents, et par conséquent, l’adaptateur doit charger le modèle au lieu d’y accéder via DTE.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Pour créer un adaptateur ModelBus qui est compatible avec les modèles de texte

1. Si la solution DSL cible n’a pas de projet **ModelBusAdapter** , créez-en une à l’aide de l’Assistant extension ModelBus :

    1. Téléchargez et installez l’extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus, si vous ne l’avez pas encore fait. Pour plus d’informations, consultez [Kit de développement logiciel de visualisation et de modélisation](https://go.microsoft.com/fwlink/?LinkID=185579).

    2. Ouvrez le fichier de définition DSL. Cliquez avec le bouton droit sur l’aire de conception, puis cliquez sur **activer ModelBus**.

    3. Dans la boîte de dialogue, sélectionnez **je souhaite exposer ce DSL au ModelBus**. Vous pouvez sélectionner les deux options si vous souhaitez que ce DSL expose ses modèles et d’utiliser des références aux autres DSL.

    4. Cliquez sur **OK**. Un nouveau projet « ModelBusAdapter » vient s'ajouter à la solution DSL.

    5. Cliquez sur **transformer tous les modèles**.

    6. Régénérez la solution.

2. Si vous souhaitez accéder au DSL à la fois à partir d’un modèle de texte et à partir d’un autre code, tel que Command, dupliquez le projet **ModelBusAdapter** :

    1. Dans l’Explorateur Windows, copiez et collez le dossier qui contient **ModelBusAdapter. csproj**.

    2. Renommez le fichier projet (par exemple, **T4ModelBusAdapter. csproj**).

    3. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, pointez sur **Ajouter**, puis cliquez sur **projet existant**. Localisez le nouveau projet d’adaptateur, **T4ModelBusAdapter. csproj**.

    4. Dans chaque `*.tt` fichier du nouveau projet, modifiez l’espace de noms.

    5. Cliquez sur le nouveau projet dans l’Explorateur de solutions, puis sur Propriétés. Dans l’éditeur de propriétés, modifiez les noms de l’assembly généré et l’espace de noms par défaut.

    6. Dans le projet DslPackage, ajoutez une référence au nouveau projet d’adaptateur afin qu’il contient des références aux deux cartes.

    7. Dans DslPackage\source.extension.tt, ajoutez une ligne qui fait référence à votre nouveau projet d’adaptateur.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformez tous les modèles** et régénérez la solution. Aucune erreur de génération ne doit se produire.

3. Dans le nouveau projet d’adaptateur, ajoutez des références aux assemblys suivants :

    - Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. Dans AdapterManager.tt :

    - Modifiez la déclaration de AdapterManagerBase afin qu’elle hérite de [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Vers la fin du fichier, remplacez l’attribut HostSpecific avant de la classe AdapterManager. Supprimez la ligne suivante :

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Insérez la ligne suivante :

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Cet attribut filtre l’ensemble de cartes est disponible lorsqu’un consommateur de modelbus recherche pour un adaptateur.

5. **Transformez tous les modèles** et régénérez la solution. Aucune erreur de génération ne doit se produire.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Écriture d’un modèle de texte qui peut résoudre les références ModelBus
 En règle générale, vous commencez avec un modèle qui lit et génère des fichiers à partir d’une « source » DSL. Ce modèle utilise la directive générée dans le projet DSL source pour lire les fichiers de modèle source de la manière décrite dans [accès aux modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md). Toutefois, le DSL source contient les références ModelBus à une DSL « cible ». Par conséquent, vous souhaitez activer le code du modèle résoudre les références et d’accéder à la cible de DSL. Vous devez par conséquent adapter le modèle en suivant ces étapes :

- Remplacez la classe de base du modèle par [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Incluez `hostspecific="true"` dans la directive de modèle.

- Ajoutez les références d’assembly pour la DSL cible et de sa carte et activer ModelBus.

- Vous n’avez pas besoin de la directive est générée dans le cadre du DSL cible.

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

 Quand ce modèle de texte est exécuté, la directive `SourceDsl` charge le fichier `Sample.source`. Le modèle peut accéder aux éléments de ce modèle, à partir de `this.ModelRoot`. Le code peut utiliser les classes de domaine et les propriétés de ce DSL.

 En outre, le modèle peut résoudre les références ModelBus. Lorsque les références pointent vers le modèle cible, les directives d’assembly permettent au code d’utiliser les classes de domaine et les propriétés du DSL de ce modèle.

- Si vous n’utilisez pas une directive qui est générée par un projet DSL, vous devez également inclure les éléments suivants.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Utilisez `this.ModelBus` pour obtenir l’accès au ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Procédure pas à pas : Test d’un modèle de texte qui utilise le ModelBus
 Dans cette procédure pas à pas, vous suivez ces étapes :

1. Construire deux DSL. Un DSL, le *consommateur*, a une propriété `ModelBusReference` qui peut faire référence à l’autre DSL, le *fournisseur*.

2. Créer deux adaptateurs ModelBus dans le fournisseur : un pour l’accès par les modèles de texte, l’autre pour du code ordinaire.

3. Créer des modèles d’instance du DSL dans un seul projet expérimental.

4. Définir une propriété de domaine dans un seul modèle pour pointer vers l’autre modèle.

5. Écrire un gestionnaire de double-clic qui ouvre le modèle qui est indiqué.

6. Écrire un modèle de texte qui peut charger le premier modèle, suivez la référence à l’autre modèle et lire l’autre modèle.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Construire une solution DSL qui est accessible au ModelBus

1. Créer une solution DSL. Pour cet exemple, sélectionnez le modèle de solution flux de tâches. Définissez le nom de la langue sur `MBProvider` et l’extension de nom de fichier sur « . fournir ».

2. Dans le diagramme de définition DSL, cliquez avec le bouton droit sur une partie vide du diagramme qui ne se trouve pas près du haut, puis cliquez sur **activer ModelBus**.

   - Si vous ne voyez pas **activer ModelBus**, vous devez télécharger et installer l’extension VMSDK ModelBus. Recherchez-le sur le site VMSDK : [Kit de développement logiciel de visualisation et de modélisation](https://go.microsoft.com/fwlink/?LinkID=185579).

3. Dans la boîte de dialogue **activer ModelBus** , sélectionnez **exposer ce DSL au ModelBus**, puis cliquez sur **OK**.

    Un nouveau projet, `ModelBusAdapter`, est ajouté à la solution.

   Vous disposez maintenant d’une solution DSL qui est accessible par les modèles de texte via ModelBus. Références à ce dernier peuvent être résolus dans le code de commandes, gestionnaires d’événements ou des règles, qui fonctionnent dans l’AppDomain de l’éditeur de fichier de modèle. Cependant, les modèles de texte dans un AppDomain séparé et ne peut pas accéder à un modèle lorsqu’il est modifié. Si vous souhaitez accéder aux références ModelBus à ce DSL à partir d’un modèle de texte, vous devez disposer d’un ModelBusAdapter distinct.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Pour créer un adaptateur ModelBus configuré pour les modèles de texte

1. Dans l’Explorateur Windows, copiez et collez le dossier qui contient ModelBusAdapter.csproj.

    Nommez le dossier T4ModelBusAdapter.

    Renommez le fichier projet T4ModelBusAdapter.csproj.

2. Dans l’Explorateur de solutions, ajoutez T4ModelBusAdapter à la solution MBProvider. Cliquez avec le bouton droit sur le nœud de la solution, pointez sur **Ajouter**, puis cliquez sur **projet existant**.

3. Cliquez sur le nœud de projet T4ModelBusAdapter, puis sur Propriétés. Dans la fenêtre Propriétés du projet, modifiez le nom de l' **assembly** et l' **espace de noms par défaut** en `Company.MBProvider.T4ModelBusAdapters`.

4. Dans chaque fichier *.tt T4ModelBusAdapter, insérer « T4 » dans la dernière partie de l’espace de noms, afin que la ligne ressemble à ce qui suit.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. Dans le projet `DslPackage`, ajoutez une référence de projet à `T4ModelBusAdapter`.

6. Dans DslPackage\source.extension.tt, ajoutez la ligne suivante sous `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. Dans le projet `T4ModelBusAdapter`, ajoutez une référence à : **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**

8. Ouvrez T4ModelBusAdapter\AdapterManager.tt :

   1. Remplacez la classe de base de AdapterManagerBase par [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Cette partie du fichier ressemble maintenant à ce qui suit.

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

   2. Vers la fin du fichier, insérez l’attribut suivant supplémentaire devant la classe AdapterManager.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Le résultat ressemble à ce qui suit.

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

9. Cliquez sur **transformer tous les modèles** dans la barre de titre de Explorateur de solutions.

10. Régénérez la solution. Cliquez sur F5.

11. Vérifiez que la solution DSL fonctionne en appuyant sur F5. Dans le projet expérimental, ouvrez `Sample.provider`. Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

    Les références ModelBus à ce DSL peut maintenant être résolus dans les modèles de texte et également dans du code ordinaire.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construire une solution DSL avec une propriété de domaine de ModelBus référence

1. Créer un nouveau langage DSL à l’aide du modèle de solution de langage Minimal. Nom de la langue MBConsumer et définir l’extension de nom de fichier « .consume ».

2. Dans le projet DSL, ajoutez une référence à l’assembly MBProvider DSL. Cliquez avec le bouton droit sur `MBConsumer\Dsl\References`, puis cliquez sur **Ajouter une référence**. Sous l’onglet **Parcourir** , recherchez `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Cela vous permet de vous permettent de créer du code qui utilise l’autres DSL. Si vous souhaitez créer des références à plusieurs DSL, ajoutez-les également.

3. Dans le diagramme de définition DSL, cliquez avec le bouton droit sur le diagramme, puis cliquez sur **activer ModelBus**. Dans la boîte de dialogue, sélectionnez **activer ce DSL pour utiliser le ModelBus**.

4. Dans la `ExampleElement`de la classe, ajoutez une nouvelle propriété de domaine `MBR`et, dans le Fenêtre Propriétés, définissez son type sur `ModelBusReference`.

5. Cliquez avec le bouton droit sur la propriété de domaine dans le diagramme, puis cliquez sur **modifier les propriétés spécifiques d’ModelBusReference**. Dans la boîte de dialogue, sélectionnez **un élément de modèle**.

    Définir le filtre de boîte de dialogue de fichier à ce qui suit.

    `Provider File|*.provide`

    La sous-chaîne après «&#124;» est un filtre pour la boîte de dialogue de sélection de fichier. Vous pouvez le définir de façon à autoriser tous les fichiers à l’aide de *.\*

    Dans la liste **type d’élément de modèle** , entrez les noms d’une ou de plusieurs classes de domaine dans le fournisseur DSL (par exemple, Company. MBProvider. Task). Ils peuvent être des classes abstraites. Si vous ne renseignez pas la liste, l’utilisateur peut définir la référence à n’importe quel élément.

6. Fermez la boîte de dialogue et **transformez tous les modèles**.

   Vous avez créé une solution DSL qui peut contenir des références aux éléments dans un autre DSL.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Créer une référence ModelBus à un autre fichier dans la solution

1. Dans la solution MBConsumer, appuyez sur CTRL + F5. Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] s’ouvre dans le projet **MBConsumer\Debugging** .

2. Ajoutez une copie de l’exemple. fournissez au projet **MBConsumer\Debugging** . Cela est nécessaire, car une référence ModelBus doit faire référence à un fichier dans la même solution.

   1. Cliquez avec le bouton droit sur le projet de débogage, pointez sur **Ajouter**, puis cliquez sur **élément existant**.

   2. Dans la boîte de dialogue **Ajouter un élément** , définissez le filtre sur **tous les fichiers (\*.\*)** .

   3. Accédez à `MBProvider\Debugging\Sample.provide`, puis cliquez sur **Ajouter**.

3. Ouvrez `Sample.consume`.

4. Cliquez sur une forme d’exemple, puis dans la fenêtre Propriétés, cliquez sur **[...]** dans la propriété MBR. Dans la boîte de dialogue, cliquez sur **Parcourir** , puis sélectionnez `Sample.provide`. Dans la fenêtre d’éléments, développez le type de tâche, puis sélectionnez l’un des éléments.

5. Enregistrez le fichier.

    (Ne fermez pas encore l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].)

   Vous avez créé un modèle qui contient une référence ModelBus à un élément dans un autre modèle.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Résoudre une ModelBus référence dans un modèle de texte

1. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez un exemple de fichier de modèle de texte. Définissez son contenu comme suit.

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

    1. Les attributs `hostSpecific` et `inherits` de la directive `template` doivent être définis.

    2. Le modèle de consommateur est accessible de la manière habituelle via le processeur de directive qui a été générée dans ce DSL.

    3. Les directives d’assembly et l’importation doivent être en mesure d’accéder ModelBus et les types du fournisseur DSL.

    4. Si vous savez que les nombreux MBR est liés au même modèle, il est préférable d’appeler CreateAdapter qu’une seule fois.

2. Enregistrez le modèle. Vérifiez que le fichier texte qui en résulte ressemble à ce qui suit.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Résoudre une référence ModelBus dans un gestionnaire de mouvements

1. Fermez l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], si elle est en cours d’exécution.

2. Ajoutez un fichier nommé MBConsumer\Dsl\Custom.cs et définissez son contenu à ce qui suit.

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

3. Appuyez sur CTRL+F5.

4. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez `Debugging\Sample.consume`.

5. Double-cliquez sur une forme.

     Si vous avez défini le MBR sur cet élément, le modèle référencé s’ouvre et l’élément référencé est sélectionné.

## <a name="see-also"></a>Voir aussi
 [Intégration de modèles à l’aide de la génération de code Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [et des modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)
