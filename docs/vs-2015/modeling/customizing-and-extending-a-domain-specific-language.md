---
title: Personnalisation et extension d’un langage spécifique à un domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1dc596909862c2ebb490fa478e1f5f71f88dd7ac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106642"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personnalisation et extension d'un langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio de modélisation et de visualisation Kit de développement logiciel (SDK) VISUALIZATION fournit plusieurs niveaux à laquelle vous pouvez définir des outils de modélisation :  
  
1. Définir un langage spécifique à un domaine (DSL) à l’aide du diagramme de définition DSL. Vous pouvez rapidement créer une solution DSL avec une notation visuelle, un formulaire XML lisible et les outils de base qui sont requises pour générer le code et autres artefacts.  
  
     Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  
  
2. Affinez la solution DSL à l’aide de fonctionnalités plus avancées de la définition DSL. Par exemple, vous pouvez ajouter des liens supplémentaires lorsque l’utilisateur crée un élément. Ces techniques sont principalement réalisées dans la définition DSL et certaines nécessitent quelques lignes de code de programme.  
  
3. Étendez vos outils de modélisation à l’aide du code de programme. Le Kit VMSDK a été conçu spécifiquement pour simplifier l'intégration à vos extensions avec le code généré à partir de la définition DSL.  Pour plus d’informations, consultez [écriture du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Lorsque vous avez mis à jour le fichier de définitions DSL, n’oubliez pas de cliquer sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions avant de régénérer votre solution.  
  
## <a name="customShapes"></a> Dans cette Section  
  
|Pour obtenir cet effet|Reportez-vous à cette rubrique|  
|----------------------------|-------------------------|  
|Autoriser l’utilisateur à définir les propriétés de couleur et le style de la forme.|Avec le bouton droit de la classe de forme ou le lien, pointez sur **ajouter les objets exposés**, cliquez sur un élément.<br /><br /> Consultez [personnaliser la présentation du diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Différentes classes d’élément de modèle se présenter comme sur le diagramme, partage des propriétés telles que la hauteur initiale et la largeur, la couleur, info-bulles.|Utiliser l’héritage entre les formes ou des classes de connecteur. Mappages entre les formes dérivées et les classes de domaine dérivées héritent les détails de mappage des parents.<br /><br /> Ou bien, mapper les classes de domaine différent à la même classe de forme.|  
|Une classe d’élément de modèle est affichée par les contextes de différentes formes.|Mapper plusieurs classes de forme à la même classe de domaine. Lorsque vous générez la solution, suivez le rapport d’erreurs et fournissez le code demandé pour décider quelle forme à utiliser.|  
|Couleur de la forme ou autres fonctionnalités telles que police indiquent l’état actuel.|Consultez [mise à jour des formes et connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Créer une règle qui met à jour les propriétés exposées. Consultez [règles de propagent de modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Ou bien, utilisez OnAssociatedPropertyChanged() pour mettre à jour non exposé des fonctionnalités telles que les flèches de lien ou de la police.|  
|Icône sur change de forme pour indiquer l’état.|Définir la visibilité du mappage de décorateur dans la fenêtre Détails DSL. Recherchez plusieurs décorateurs d’image sur la même position. Consultez [mise à jour des formes et connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Ou substituer `ImageField.GetDisplayImage()`. Consultez l’exemple dans <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Définir une image d’arrière-plan sur n’importe quelle forme|Substituer InitializeInstanceResources() pour ajouter un ImageField ancré. Consultez [personnaliser la présentation du diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Imbriquer des formes à n’importe quelle profondeur|Configurer une récursive incorporation d’arborescence. Définir par BoundsRules pour qu’il contienne les formes. Consultez [personnaliser la présentation du diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Rattachez des connecteurs à des points fixes sur les limites d’un élément.|Définir les éléments terminal incorporés, représentés par petits ports sur le diagramme. Utilisez BoundsRules pour corriger les ports en place. Consultez l’exemple de diagramme de Circuit dans [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Champ de texte affiche une valeur dérivée d’autres valeurs.|Mapper le décorateur de texte à une propriété de domaine calculé ou le stockage personnalisé. Pour plus d’informations, consultez [calculées et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).|  
|Propager les modifications entre les éléments de modèle, ou entre les formes|Consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).|  
|Propager les modifications apportées aux ressources telles que les autres [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensions en dehors du magasin.|Consultez [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Fenêtre Propriétés affiche les propriétés d’un élément associé.|Configurer le transfert de propriété. Consultez [personnalisation de la fenêtre Propriétés](../modeling/customizing-the-properties-window.md).|  
|Catégories de propriétés|La fenêtre Propriétés est divisée en sections appelées des catégories. Définir le **catégorie** de propriétés de votre domaine. Propriétés portant le même nom de catégorie apparaîtront dans la même section. Vous pouvez également définir le **catégorie** d’un rôle de relation.|  
|Contrôler l’accès utilisateur aux propriétés de domaine|Définissez **Is Browsable** false pour empêcher une propriété de domaine dans la fenêtre Propriétés au moment de l’exécution. Vous pouvez toujours le mapper à des éléments décoratifs de texte.<br /><br /> **Est l’interface utilisateur en lecture seule** empêche les utilisateurs de modifier une propriété de domaine.<br /><br /> Programme d’accéder à la propriété de domaine n’est pas affectée.|  
|Modifier le nom, une icône et une visibilité de nœuds dans l’Explorateur de modèles de votre solution DSL.|Consultez [personnalisation de l’Explorateur de modèles](../modeling/customizing-the-model-explorer.md).|  
|Activer le copier, couper et coller|Définir le **activer copier coller** propriété de la **éditeur** nœud dans l’Explorateur DSL.|  
|Copier leurs objectifs et les liens de référence chaque fois qu’un élément est copié. Par exemple, copiez les commentaires associés à un élément.|Définir le **propage la copie** la propriété du rôle source (représenté par la ligne de chaque côté de la relation de domaine dans le diagramme de définition DSL).<br /><br /> Écrire du code pour remplacer ProcessOnCopy pour obtenir des effets plus complexes.<br /><br /> Consultez [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Supprimer, redéfinir la parenté ou relier des éléments connexes lorsqu’un élément est supprimé.|Définir le **Propagates Delete** valeur d’un rôle de relation. Pour obtenir des effets plus complexes, remplacer `ShouldVisitRelationship` et `ShouldVisitRolePlayer` méthodes dans le `MyDslDeleteClosure` (classe), définie dans **DomainModel.cs**<br /><br /> Consultez [personnalisation du comportement de suppression](../modeling/customizing-deletion-behavior.md)|  
|Conserver la disposition des formes et l’apparence sur la copie et de glisser-déplacer.|Ajouter les formes et connecteurs pour copié `ElementGroupPrototype`. Est la méthode la plus commode de substitution `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consultez [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Coller des formes à un emplacement choisi, par exemple la position actuelle du curseur.|Substituer `ClipboardCommandSet.ProcessOnCopy()` à utiliser la version spécifique à l’emplacement de `ElementOperations.Merge().` consultez [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Créer des liens supplémentaires lors du collage|Override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Activer le glisser-déplacer à partir de ce diagramme, autres UML ou DSL diagrammes et les éléments de Windows|Voir [Guide pratique pour ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Autoriser une forme ou un outil soit glissée vers une forme enfant, tel qu’un port, comme s’il était de faire glisser le parent.|Définir une Directive de fusion sur la classe d’objet cible, pour transférer l’objet déplacé vers le parent. Consultez [personnalisation de la création d’élément et le déplacement des](../modeling/customizing-element-creation-and-movement.md).|  
|Autoriser une forme ou un outil permettant de faire glisser vers une forme et des liens supplémentaires ou des objets créés. Par exemple, pour autoriser un commentaire à être déposé sur un élément auquel il doit être lié.|Définir une Directive de fusion sur la classe de domaine cible et définir les liens à générer. Dans les cas complexes, vous pouvez ajouter le code personnalisé. Consultez [personnalisation de la création d’élément et le déplacement des](../modeling/customizing-element-creation-and-movement.md).|  
|Créer un groupe d’éléments avec un seul outil. Par exemple, un composant avec un ensemble fixe de ports.|Substituez la méthode d’initialisation de boîte à outils de ToolboxHelper.cs. Créer un Prototype de groupe élément (EGP) contenant les éléments et leurs liens de relation. Consultez [personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Inclure les formes principal et le ports dans l’EGP, soit définir BoundsRules pour positionner les formes de port lorsque l’EGP est instancié. Consultez [emplacement de la forme et la taille de contrainte par BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Utilisez un outil de connexion pour instancier plusieurs types de relation.|Ajoutez les Directives de connexion de lien (LCD) pour le Générateur de connexion qui est appelé par l’outil. Les écrans LCD déterminent le type de la relation à partir des types des deux éléments. Pour en faire varient selon les États des éléments, vous pouvez ajouter le code personnalisé. Consultez [personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).|  
|Outils rémanentes – l’utilisateur peut double-cliquer sur n’importe quel outil pour créer de nombreuses formes ou des connecteurs à la suite.|Dans l’Explorateur DSL, sélectionnez le `Editor` nœud. Dans la fenêtre Propriétés, définissez **utilise des éléments de boîte à outils rémanentes**.|  
|Définir des commandes de menu|Voir [Guide pratique pour modifier une commande de menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Limiter le modèle avec des règles de validation|Consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)|  
|Générer le code, les fichiers de configuration ou les documents à partir d’un DSL.|[Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personnaliser la façon dont les modèles sont enregistrés au fichier.|Consultez [personnalisation du stockage de fichier et de sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Enregistrer les modèles dans les bases de données ou tout autre média.|Substituer *Votre_langage*DocData<br /><br /> Consultez [personnalisation du stockage de fichier et de sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Intégrer plusieurs DSL afin qu’ils fonctionnent en tant que partie d’une application.|Consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Votre solution DSL d’être étendue par des tiers et de contrôler l’extension.|[Étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Partage de classes entre plusieurs DSL à l’aide d’une bibliothèque DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Définition d’une stratégie de verrouillage pour créer des segments en lecture seule](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)   
 [Écriture de Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
