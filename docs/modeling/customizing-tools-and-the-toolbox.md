---
title: Personnalisation des outils et de la boîte à outils
description: Découvrez comment vous devez définir des éléments de boîte à outils pour les éléments que vous souhaitez permettre aux utilisateurs d’ajouter à leurs modèles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 956955a9c2feb9982bee0101965336be2ca29ab7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385810"
---
# <a name="customizing-tools-and-the-toolbox"></a>Personnalisation des outils et de la boîte à outils

Vous devez définir les éléments de boîte à outils pour les éléments que les utilisateurs sont autorisés à ajouter à leurs modèles. Il existe deux types d'outils : les outils d'élément et les outils de connexion. Dans le concepteur généré, un utilisateur peut sélectionner un outil d'élément pour déplacer des formes vers le diagramme et sélectionner un outil de connexion pour tracer des liens entre les formes. En général, les outils d'élément permettent aux utilisateurs d'ajouter des instances de classes de domaine à leurs modèles et les outils de connexion d'ajouter des instances de relations de domaine.

## <a name="how-the-toolbox-is-defined"></a><a name="ToolboxDef"></a> Définition de la boîte à outils
 Dans l'Explorateur DSL, développez le nœud Éditeur et les nœuds sous-jacents. Généralement, vous voyez une arborescence qui se présente ainsi :

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

Dans cette partie de l'Explorateur DSL, vous pouvez :

- Créer des onglets. Les onglets définissent les en-têtes de section de la boîte à outils.

- Créer des outils.

- Copier et coller des outils.

- Monter ou descendre des outils dans la liste.

- Supprimer des onglets et des outils.

> [!IMPORTANT]
> Pour ajouter ou coller des éléments dans un Explorateur DSL, cliquez avec le bouton droit sur le grand-parent du nouveau nœud. Par exemple, pour ajouter un outil, cliquez avec le bouton droit sur l’onglet, et non sur le nœud **Outils** . Pour ajouter un onglet, cliquez avec le bouton droit sur le nœud de l' **éditeur** .

La propriété **icône de boîte à outils** de chaque outil référence un fichier bitmap 16x16. Ces fichiers sont généralement conservés dans le dossier **Dsl\Resources**

La propriété de **classe** d’un outil d’élément fait référence à une classe de domaine concrète. Par défaut, l'outil crée les instances de cette classe. Cependant, vous pouvez écrire le code pour que l'outil crée des groupes d'éléments ou des éléments de différents types.

La propriété **Générateur de connexions** d’un outil de connexion fait référence à un générateur de connexions, qui définit les types d’éléments que l’outil peut connecter et les relations qu’il crée entre eux. Les générateurs de connexions sont définis comme nœuds dans l'Explorateur DSL. Les générateurs de connexions sont créés automatiquement lorsque vous définissez les relations de domaine, mais vous pouvez écrire le code qui permet de les personnaliser.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Pour ajouter un outil à la boîte à outils

1. Vous créez généralement un outil d'élément après avoir créé une classe de formes et l'avoir mappée sur une classe de domaines.

     Vous créez généralement un outil de connecteur après avoir créé une classe de connecteurs et l'avoir mappée sur une relation de référence.

2. Dans l’Explorateur DSL, développez le nœud **éditeur** et le nœud **onglets de boîte à outils** .

     Cliquez avec le bouton droit sur un nœud d’onglet de boîte à outils, puis cliquez sur **Ajouter un nouvel élément** ou **Ajouter un nouvel outil de connexion**.

3. Définissez la propriété **icône de boîte à outils** pour faire référence à une image bitmap 16x16.

     Si vous souhaitez définir une nouvelle icône, créez un fichier bitmap dans Explorateur de solutions dans le dossier **Dsl\Resources** . Le fichier doit avoir les valeurs de propriété suivantes : générer le contenu de l' **action**  =  ; **Copier dans le répertoire**  =  de sortie **Ne pas copier**.

4. **Pour un outil d’élément :** Définissez la propriété de **classe** de l’outil pour faire référence à une classe de domaine concrète qui est mappée à une forme.

     **Pour un outil de connecteur :** Définissez la propriété **Générateur de connexions** de l’outil sur l’un des éléments proposés dans la liste déroulante. Les générateurs de connexions sont automatiquement créés lorsque vous mappez un connecteur sur une relation de domaine. Si vous avez créé récemment un connecteur, vous devez normalement sélectionner le générateur de connexions associé.

5. Pour tester le DSL, appuyez sur F5 ou CTRL + F5, et dans l’instance expérimentale de Visual Studio, ouvrez un exemple de fichier de modèle. Le nouvel outil doit apparaître sur la boîte à outils. Faites-le glisser vers le diagramme pour vérifier qu'un nouvel élément a été créé.

     Si l’outil n’apparaît pas, arrêtez Visual Studio expérimental. Dans le menu **Démarrer** de Windows, exécutez **Reset the Microsoft Visual Studio instance expérimentale 2010**. Dans le menu **Générer**, cliquez sur **Régénérer la solution**. Puis, testez à nouveau le DSL.

## <a name="customizing-element-tools"></a><a name="customizing"></a> Personnalisation des outils d’élément
 Par défaut, l'outil crée une seule instance de la classe spécifiée, mais vous pouvez modifier ce comportement de deux façons :

- Définissez Directives de fusion d'éléments sur d'autres classes, en leur permettant d'accepter de nouvelles instances de cette classe et de créer des liens supplémentaires lorsque le nouvel élément est créé. Par exemple, vous pouvez autoriser l'utilisateur à déposer un Commentaire sur un autre élément et à créer ainsi un lien de référence entre les deux éléments.

     Ces personnalisations affectent aussi ce qui se passe quand l'utilisateur colle ou fait glisser un élément.

     Pour plus d’informations, consultez Personnalisation de la [création et du déplacement d’éléments](../modeling/customizing-element-creation-and-movement.md).

- Écrivez le code pour personnaliser l'outil de telle sorte qu'il puisse créer des groupes d'éléments. L'outil est initialisé par des méthodes de ToolboxHelper.cs que vous pouvez remplacer. Pour plus d’informations, consultez [création de groupes d’éléments à partir d’un outil](#groups).

## <a name="creating-groups-of-elements-from-a-tool"></a><a name="groups"></a> Création de groupes d’éléments à partir d’un outil
 Chaque outil d'élément contient un prototype des éléments qu'il doit créer. Par défaut, chaque outil d'élément crée un seul élément, mais il est également possible de créer un groupe d'objets liés avec un seul outil. Pour ce faire, vous initialisez l'outil avec un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> qui contient les éléments liés.

 L'exemple suivant est extrait d'un DSL dans lequel se trouve un type Transistor. Chaque Transistor possède trois Terminaux nommés. L'outil d'élément pour Transistors stocke un prototype contenant quatre éléments de modèle et trois liens de relation. Lorsque l'utilisateur déplace l'outil sur le diagramme, le prototype est instancié et lié à la racine du modèle.

 Ce code substitue une méthode définie dans **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Pour plus d’informations sur la personnalisation du modèle à l’aide de code de programme, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="customizing-connection-tools"></a><a name="connections"></a> Personnalisation des outils de connexion
 Généralement, vous créez un outil d'élément lorsque vous créez une classe de connecteurs. Une autre solution consiste à surcharger un outil en autorisant les types des deux extrémités à déterminer le type de la relation. Par exemple, vous pouvez définir un outil de connexion capable de créer à la fois des relations de type Personne-Personne et des relations de type Personne-Ville.

 Les outils de connexion invoquent les générateurs de connexions. Utilisez les générateurs de connexions pour spécifier de quelle façon les utilisateurs peuvent lier les éléments dans le concepteur généré. Les générateurs de connexions spécifient les éléments qui peuvent être liés et le type de lien créé entre eux.

 Lorsque vous créez une relation de référence entre classes de domaine, un générateur de connexions est automatiquement créé. Vous pouvez utiliser ce générateur de connexions lors du mappage d'un outil de connexion. Pour plus d’informations sur la création d’outils de connexion, consultez [configuration de la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).

 Vous pouvez modifier le générateur de connexions par défaut de telle sorte qu'il puisse traiter un éventail différent de types source et cible, et créer différents types de relation.

 Vous pouvez aussi écrire le code personnalisé des générateurs de connexions pour spécifier les classes source et cible de la collection, définir le type de connexion à établir et déclencher d'autres actions associées à la création d'une connexion.

### <a name="the-structure-of-connection-builders"></a>Structure des générateurs de connexions
 Les générateurs de connexions contiennent une ou plusieurs directives de connexion de liens, qui spécifient la relation de domaine et les éléments source et cible. Par exemple, dans le modèle de solution de déroulement des tâches, vous pouvez voir le **CommentReferencesSubjectsBuilder** dans l' **Explorateur DSL**. Ce générateur de connexions contient une directive de connexion de lien nommée **CommentReferencesSubjects**, qui est mappée à la relation de domaine **CommentReferencesSubjects**. Cette directive de connexion de liens contient une directive de rôle source qui pointe vers la classe de domaine `Comment` et une directive de rôle cible qui pointe vers la classe de domaine `FlowElement`.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Utilisation de générateurs de connexion pour limiter les rôles source et cible
 Vous pouvez utiliser les générateurs de connexion pour restreindre l'occurrence de certaines classes dans le rôle source ou le rôle cible d'une relation de domaine donnée. Par exemple, il se peut que vous ayez une classe de domaine de base avec une relation de domaine vers une autre classe de domaine, mais que vous ne vouliez pas que toutes les classes dérivées de la classe de base aient les mêmes rôles dans cette relation. Dans la solution de workflow de tâches, il existe quatre classes de domaine concretes (**StartPoint**, **Endpoint**, **MergeBranch** et **Synchronization**) qui héritent directement de la classe de domaine abstraite **FlowElement**, et de deux classes de domaine concrètes (**Task** et **ObjectInState**) qui héritent indirectement de celle-ci. Il existe également une relation de référence de **Flow** qui prend les classes de domaine **FlowElement** dans son rôle source et son rôle cible. Toutefois, une instance d’une classe de domaine de **point de terminaison** ne doit pas être la source d’une instance d’une relation de **Flow** , et une instance d’une classe **StartPoint** ne doit pas être la cible d’une instance d’une relation **Flow** . Le générateur de connexions **FlowBuilder** dispose d’une directive de connexion de lien nommée **Flow** qui spécifie les classes de domaine qui peuvent jouer le rôle source (**tâche**, **MergeBranch**, **StartPoint** et **synchronisation**) et qui peuvent jouer le rôle cible (**MergeBranch**, **point de terminaison** et **synchronisation**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Générateurs de connexions avec plusieurs directives de connexion de liens
 Vous pouvez ajouter plusieurs directives de connexion de liens à un générateur de connexions. Cela peut vous aider à masquer certaines des complexités du modèle de domaine aux utilisateurs et à éviter que la **boîte à outils** ne soit trop encombrée. Vous pouvez ajouter les directives de connexion de liens de différentes relations de domaine à un seul générateur de connexions. Cependant, vous devez regrouper les relations de domaine quand elles exécutent à peu près la même fonction.

 Dans la solution de workflow de tâches, l’outil **Flow** Connection est utilisé pour dessiner des instances des relations de domaine **Flow** et **ObjectFlow** . Le générateur de connexions **FlowBuilder** a, en plus de la directive de connexion de lien de **Flow** décrite précédemment, deux directives de connexion de lien nommées **ObjectFlow**. Ces directives spécifient qu’une instance d’une relation **ObjectFlow** peut être dessinée entre des instances de la classe de domaine **ObjectInState** , ou d’une instance d’un **ObjectInState** à une instance d’une **tâche, mais** pas entre deux instances d’une **tâche**, ou d’une instance d’une **tâche** à une instance d’un **ObjectInState**. Toutefois, une instance d’une relation de **Flow** peut être dessinée entre deux instances d’une **tâche**. Si vous compilez et exécutez la solution de déroulement des tâches, vous pouvez voir que le dessin d’un **Workflow** à partir d’une instance d’un **ObjectInState** vers une instance d’une **tâche** crée une instance d’un **ObjectFlow**, mais le dessin d’un **Workflow** entre deux instances d’une **tâche** crée une instance d’un **fluide**.

### <a name="custom-code-for-connection-builders"></a>Code personnalisé pour générateurs de connexions
 Les quatre cases à cocher de l'interface utilisateur définissent différents types de personnalisation de générateurs de connexions :

- la case à cocher **acceptation personnalisée** dans une directive de rôle source ou cible

- case à cocher **connexion personnalisée** dans une directive de rôle source ou cible

- la case à cocher **utilise la connexion personnalisée** dans une directive de connexion

- la propriété **est personnalisé** du générateur de connexions

  Vous devez écrire un certain code de programme pour procéder à ces personnalisations. Pour savoir quel code vous devez fournir, cochez l'une de ces cases, cliquez sur Transformer tous les modèles, puis générez votre solution. Il en résultera un rapport d'erreurs. Double-cliquez sur le rapport d'erreurs pour afficher un commentaire expliquant quel code vous devez ajouter.

> [!NOTE]
> Pour ajouter un code personnalisé, créez une définition de classe partielle dans un fichier de code distinct des fichiers de code des dossiers GeneratedCode. Pour éviter de perdre votre travail, vous ne devez pas modifier les fichiers de code générés. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Création du code de connexion personnalisé
 Dans chaque directive de connexion de lien, l’onglet **directives de rôle source** définit à partir des types que vous pouvez faire glisser. De même, l’onglet **directives de rôle cible** définit les types que vous pouvez faire glisser. Pour chaque type, vous pouvez spécifier s’il faut autoriser la connexion (pour cette directive de connexion de lien) en définissant l’indicateur d' **acceptation personnalisée** , puis en fournissant le code supplémentaire.

 Vous pouvez également personnaliser ce qui se produit quand la connexion est établie. Par exemple, vous pouvez personnaliser uniquement le cas où le déplacement se produit vers ou depuis une classe particulière, tous les cas commandés par une directive de connexion de liens ou la totalité du générateur de connexions FlowBuilder. Pour chacune de ces options, vous pouvez définir des indicateurs personnalisés au niveau approprié. Lorsque vous transformez tous les modèles et essayez de générer la solution, les messages d'erreur vous dirigent vers les commentaires qui se trouvent dans le code généré. Ces commentaires identifient ce que vous devez fournir.

 Dans l'exemple Diagramme de composants, le générateur de connexions de la relation de domaine Connexion est personnalisé pour limiter les connexions qui peuvent être établies entre les ports. L'illustration suivante montre que vous ne pouvez établir des connexions qu'à partir des éléments `OutPort` vers les éléments `InPort`, mais que vous pouvez imbriquer des composants les uns à l'intérieur des autres.

 **Connexion entrante vers un OutPort à partir d'un composant imbriqué**

 ![Générateur de connexions](../modeling/media/connectionbuilder_3.png)

 Par conséquent, il se peut que vous vouliez spécifier qu'une connexion puisse aller d'un composant imbriqué vers un OutPort. Pour spécifier une telle connexion, vous définissez **utilise l’acceptation personnalisée** sur le type d' **inport** comme rôle source et le type de **port** comme rôle cible dans la fenêtre **Détails DSL** , comme indiqué dans les illustrations suivantes :

 **Directive de connexion de liens dans l'Explorateur DSL**

 ![Image du générateur de connexions](../modeling/media/connectionbuilder_4a.png)

 **Directive de connexion de liens dans la fenêtre Détails DSL**

 ![Directive de connexion de lien dans la fenêtre Détails DSL](../modeling/media/connectionbuilder_4b.png)

 Vous devez ensuite fournir les méthodes de la classe ConnectionBuilder :

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Pour plus d’informations sur la personnalisation du modèle à l’aide de code de programme, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Vous pouvez utiliser un code similaire pour empêcher, par exemple, les utilisateurs de créer des boucles avec des liens parent-enfant. Ces restrictions sont considérées comme des contraintes « dures », car les utilisateurs ne peuvent pas les violer à tout moment. Vous pouvez également créer des contrôles de validation « soft » que les utilisateurs peuvent contourner temporairement en créant des configurations non valides qu’ils ne peuvent pas enregistrer.

### <a name="good-practice-in-defining-connection-builders"></a>Meilleure pratique de définition des générateurs de connexions
 Vous devez définir un générateur de connexions pour créer différents types de relation uniquement s'ils sont conceptuellement associés. Dans l'exemple du flux de tâches, vous utilisez le même générateur pour créer des flux entre les tâches, ainsi qu'entre les tâches et les objets. Cependant, l'utilisation du même générateur pour créer des relations entre commentaires et tâches serait source de confusion.

 Si vous définissez un générateur de connexions pour plusieurs types de relation, vous devez vous assurer qu'il ne puisse pas correspondre à plus d'un type de la même paire d'objets source et cible. Sinon, les résultats seront imprévisibles.

 Vous utilisez du code personnalisé pour appliquer des contraintes « dures », mais vous devez déterminer si les utilisateurs doivent être en mesure de créer temporairement des connexions non valides. S'ils le peuvent, vous pouvez modifier les contraintes de telle sorte que les connexions ne soient pas validées tant que les utilisateurs n'ont pas enregistré les modifications.

## <a name="see-also"></a>Voir aussi

- [Personnalisation de la création et du mouvement des éléments](../modeling/customizing-element-creation-and-movement.md)
- [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)
- [Guide pratique pour ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Exemple de diagrammes de circuit DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
