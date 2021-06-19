---
title: Personnalisation et extension d'un langage spécifique à un domaine
description: Découvrez comment le kit de développement logiciel (SDK) de modélisation et de visualisation de Visual Studio fournit plusieurs niveaux à partir desquels vous pouvez définir des outils de modélisation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389382"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Personnaliser et étendre un langage spécifique à un domaine

Le kit de développement logiciel (SDK) de modélisation et de visualisation de Visual Studio fournit plusieurs niveaux à partir desquels vous pouvez définir des outils de modélisation :

1. Définissez un langage spécifique à un domaine (DSL) à l’aide du diagramme de définition DSL. Vous pouvez rapidement créer un DSL avec une notation schématique, un formulaire XML lisible et les outils de base requis pour générer du code et d’autres artefacts. Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

2. Ajustez la DSL en utilisant des fonctionnalités plus avancées de la définition DSL. Par exemple, vous pouvez faire apparaître des liens supplémentaires lorsque l’utilisateur crée un élément. Ces techniques sont principalement obtenues dans la définition DSL, et certaines nécessitent quelques lignes de code de programme.

3. Étendez vos outils de modélisation à l’aide du code de programme. Le Kit VMSDK a été conçu spécifiquement pour simplifier l'intégration à vos extensions avec le code généré à partir de la définition DSL. Pour plus d’informations, consultez [écriture de code pour personnaliser un langage de Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Lorsque vous avez mis à jour le fichier de définitions DSL, n’oubliez pas de cliquer sur **transformer tous les modèles** dans la barre d’outils de **Explorateur de solutions** avant de reconstruire votre solution.

## <a name="article-reference"></a>Référence de l’article

|Pour obtenir cet effet|Reportez-vous à cette rubrique|
|-|-|
|Permet à l’utilisateur de définir les propriétés de couleur et de style d’une forme.|Cliquez avec le bouton droit sur la classe de forme ou de connecteur, pointez sur **Ajouter exposé**, puis cliquez sur un élément.|
|Différentes classes d’élément de modèle ressemblent au diagramme, en partageant des propriétés telles que la hauteur et la largeur initiales, la couleur, les info-bulles.|Utilisez l’héritage entre les formes ou les classes de connecteur. Les mappages entre les formes dérivées et les classes de domaine dérivées héritent des détails de mappage des parents.<br /><br /> Ou mappez des classes de domaine différentes à la même classe Shape.|
|Une classe d’élément de modèle est affichée par différents contextes de formes.|Mappez plusieurs classes Shape à la même classe de domaine. Lorsque vous générez la solution, suivez le rapport d’erreurs et fournissez le code demandé pour déterminer la forme à utiliser.|
|La couleur de la forme ou d’autres fonctionnalités telles que la police indiquent l’état actuel.|Consultez [mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Créez une règle qui met à jour les propriétés exposées. Consultez [règles de propagation des modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Vous pouvez aussi utiliser OnAssociatedPropertyChanged () pour mettre à jour les fonctionnalités non exposées, telles que les flèches de lien ou la police.|
|L’icône sur la forme change pour indiquer l’État.|Définissez la visibilité du mappage de l’élément décoratif dans la fenêtre Détails DSL. Localisez plusieurs décorateurs d’images à la même position. Consultez  [mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Ou substituez `ImageField.GetDisplayImage()` . Consultez l’exemple dans <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Définir une image d’arrière-plan sur n’importe quelle forme|Remplacez InitializeInstanceResources () pour ajouter un ImageField ancré.|
|Imbriquer des formes à n’importe quelle profondeur|Configurez une arborescence d’incorporation récursive. Définissez BoundsRules pour contenir les formes.|
|Attachez des connecteurs à des points fixes sur les limites d’un élément.|Définissez les éléments terminaux incorporés, représentés par de petits ports sur le diagramme. Utilisez BoundsRules pour corriger les ports en place. Consultez l’exemple de schéma de circuit dans le [Kit de développement logiciel de visualisation et de modélisation](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).|
|Champ de texte affiche une valeur dérivée d’autres valeurs.|Mappez l’élément décoratif de texte à une propriété de domaine de stockage calculée ou personnalisée. Pour plus d’informations, consultez [Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md).|
|Propager les modifications entre les éléments de modèle ou entre les formes|Consultez [validation dans un langage de Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).|
|Propage les modifications à des ressources telles que d’autres extensions Visual Studio en dehors du magasin.|Consultez [les gestionnaires d’événements pour propager les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|La fenêtre Propriétés affiche les propriétés d’un élément associé.|Configurez le transfert de propriété. Consultez [Personnalisation de la fenêtre Propriétés](../modeling/customizing-the-properties-window.md).|
|Catégories de propriétés|La fenêtre Propriétés est divisée en sections appelées catégories. Définissez la **catégorie** de vos propriétés de domaine. Les propriétés portant le même nom de catégorie s’affichent dans la même section. Vous pouvez également définir la **catégorie** d’un rôle de relation.|
|Contrôler l’accès utilisateur aux propriétés de domaine|Set **peut être exploré** false pour empêcher l’affichage d’une propriété de domaine dans la fenêtre Propriétés au moment de l’exécution. Vous pouvez toujours le mapper à des décorateurs de texte.<br /><br /> **L’interface utilisateur est en lecture seule** empêche les utilisateurs de modifier une propriété de domaine.<br /><br /> L’accès du programme à la propriété de domaine n’est pas affecté.|
|Modifiez le nom, l’icône et la visibilité des nœuds dans l’Explorateur de modèles de votre DSL.|Consultez [Personnalisation de l’Explorateur de modèles](../modeling/customizing-the-model-explorer.md).|
|Activer la copie, couper et coller|Définissez la propriété **activer la copie de collage** du nœud **éditeur** dans l’Explorateur DSL.|
|Copier les liens de référence et leurs cibles chaque fois qu’un élément est copié. Par exemple, copiez les commentaires attachés à un élément.|Définissez la propriété **propager la copie** du rôle source (représenté par la ligne d’un côté de la relation de domaine dans le diagramme de définition DSL).<br /><br /> Écrivez du code pour remplacer ProcessOnCopy pour obtenir des effets plus complexes.<br /><br /> Consultez [Personnalisation du comportement](../modeling/customizing-copy-behavior.md)de la copie.|
|Supprimer, reparenter ou réassocier des éléments connexes lorsqu’un élément est supprimé.|Définissez la valeur de **suppression des propagations** d’un rôle de relation. Pour les effets plus complexes, substituez `ShouldVisitRelationship` `ShouldVisitRolePlayer` les méthodes et dans la `MyDslDeleteClosure` classe, définies dans **DomainModel. cs**.|
|Conserver la disposition et l’apparence de la forme lors de la copie et du glisser-déplacer.|Ajoutez les formes et les connecteurs au copié `ElementGroupPrototype` . La méthode la plus pratique pour remplacer est `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consultez [Personnalisation du comportement](../modeling/customizing-copy-behavior.md)de la copie.|
|Coller des formes à un emplacement choisi, par exemple la position actuelle du curseur.|Substituez `ClipboardCommandSet.ProcessOnCopy()` pour utiliser la version spécifique à l’emplacement de `ElementOperations.Merge().` voir [Personnalisation du comportement](../modeling/customizing-copy-behavior.md)de la copie.|
|Créer des liens supplémentaires lors du collage|Remplacez ClipboardCommandSet. ProcessOnPasteCommand ()|
|Activer le glisser-déplacer à partir de ce diagramme, d’autres DSL et éléments Windows|Consultez [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Autoriser le glissement d’une forme ou d’un outil sur une forme enfant, telle qu’un port, comme si elle était glissée sur le parent.|Définissez une directive de fusion d’élément sur la classe d’objet cible pour transférer l’objet déplacé vers le parent. Consultez [Personnalisation de la création et du déplacement des éléments](../modeling/customizing-element-creation-and-movement.md).|
|Autoriser le glissement d’une forme ou d’un outil sur une forme et avoir des liens ou des objets supplémentaires créés. Par exemple, pour autoriser la suppression d’un commentaire sur un élément auquel il doit être lié.|Définissez une directive de fusion d’éléments sur la classe de domaine cible et définissez les liens à générer. Dans les cas complexes, vous pouvez ajouter du code personnalisé. Consultez [Personnalisation de la création et du déplacement des éléments](../modeling/customizing-element-creation-and-movement.md).|
|Créez un groupe d’éléments à l’aide d’un seul outil. Par exemple, un composant avec un ensemble fixe de ports.|Substituez la méthode d’initialisation Toolbox dans ToolboxHelper. cs. Créez un prototype de groupe d’éléments (EGP) contenant les éléments et leurs liens de relation. Consultez [Personnalisation des outils et de la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Incluez les formes principal et port dans le EGP, ou définissez BoundsRules pour positionner les formes de port lorsque le EGP est instancié.|
|Utilisez un outil de connexion pour instancier plusieurs types de relations.|Ajoutez des directives de connexion de lien (LCD) au générateur de connexions qui est appelé par l’outil. Les écrans LCD déterminent le type de la relation à partir des types des deux éléments. Pour que cela dépende des États des éléments, vous pouvez ajouter du code personnalisé. Consultez [Personnalisation des outils et de la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).|
|Outils rémanents : l’utilisateur peut double-cliquer sur n’importe quel outil pour créer plusieurs formes ou connecteurs successivement.|Dans l’Explorateur DSL, sélectionnez le `Editor` nœud. Dans le Fenêtre Propriétés, Set **utilise des éléments de boîte à outils rémanents**.|
|Définir des commandes de menu|Consultez [Comment : modifier une commande de menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Contraindre le modèle à l’aide de règles de validation|Voir [la validation dans un langage de Domain-Specific](../modeling/validation-in-a-domain-specific-language.md)|
|Générez du code, des fichiers de configuration ou des documents à partir d’un DSL.|[Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personnaliser la façon dont les modèles sont enregistrés dans un fichier.|Voir [Personnalisation du stockage de fichiers et de la SÉRIALISATION XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Enregistrer des modèles dans des bases de données ou d’autres médias.|Remplacer *YourLanguage* DocData<br /><br /> Voir [Personnalisation du stockage de fichiers et de la SÉRIALISATION XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Intégrer plusieurs DSL pour qu’ils fonctionnent dans le cadre d’une application.|Consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Autorisez l’extension de votre DSL par des tiers et contrôlez l’extension.|[Étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Partage de classes entre plusieurs DSL à l'aide d'une bibliothèque DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Définition d'une stratégie de verrouillage pour créer des segments en lecture seule](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)
- [Écriture de code pour personnaliser un langage de Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
