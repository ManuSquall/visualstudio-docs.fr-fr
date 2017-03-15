---
title: "Vue d’ensemble du langage spécifique au domaine outils Interface utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 25
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d76ed4d14e7333678fcf927dfa1b2f21d8573be5
ms.lasthandoff: 02/22/2017

---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Vue d'ensemble de l'interface utilisateur des outils de langage spécifique à un domaine
Lorsque vous ouvrez pour la première fois une solution d’outils de langage spécifique à un domaine (outils DSL) dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], l’interface utilisateur ressemble à l’image suivante.  
  
 ![concepteur DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 Le tableau suivant explique comment les parties de l’interface utilisateur sont utilisés.  
  
|**Élément**|**Définition**|  
|-----------------|--------------------|  
|Diagramme|Le diagramme affiche le modèle de domaine.<br /><br /> Le diagramme présente deux facettes. Côté « un » définit les types des éléments dans les modèles. L’autre côté définit l’apparaissent de vos modèles à l’écran.|  
|Boîte à outils|Faites glisser des outils à partir de la boîte à outils pour ajouter des classes de domaine et forme des types sur le diagramme. Pour ajouter des relations, les connecteurs et les mappages de formes, cliquez sur l’outil, puis cliquez sur le nœud source sur le diagramme, puis le nœud cible.|  
|explorateur DSL|**Explorateur DSL** apparaît lorsqu’une définition DSL est la fenêtre active. Il montre la solution DSL sous forme d’arborescence. Explorateur DSL vous permet de modifier les fonctionnalités du modèle qui ne sont pas affichées sur le diagramme. Par exemple, vous pouvez ajouter des éléments de boîte à outils et basculer sur le processus de validation à l’aide de la **Explorateur DSL**.|  
|Fenêtre Détails DSL|Le **détails DSL** fenêtre affiche les propriétés du domaine des éléments du modèle qui vous permettent de contrôler comment les éléments sont affichés, et comment les éléments sont copiés et supprimés.<br /><br /> : Par défaut, le **détails DSL** fenêtre apparaît en regard du **liste d’erreurs** et **sortie** windows.|  
  
## <a name="the-domain-model-diagram"></a>Le diagramme de modèle de domaine  
 Le diagramme de modèle de domaine est divisé en deux parties. Un côté du diagramme affiche les éléments et les relations dans le modèle. L’autre montre comment le modèle doit être affichée, ainsi que les formes qui sont utilisés pour afficher les éléments et les propriétés du diagramme de modèle. L’illustration suivante montre les éléments du diagramme.  
  
 ![concepteur DSL avec couloir](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Le tableau suivant décrit certains des éléments du diagramme de modèle de domaine.  
  
|**Terme**|**Définition**|  
|--------------|--------------------|  
|Classe de domaine|Classes de domaine sont les types d’éléments dans les modèles.<br /><br /> Une classe de domaine peut apparaître plusieurs fois dans un diagramme, si elle est la cible de plusieurs relations.<br /><br /> Pour ajouter une classe de domaine, faites glisser l’outil de classe de domaine à partir de la **boîte à outils** à la **Classes et relations** côté du diagramme.|  
|Relation de domaine|Relations de domaine sont les types de liens entre des éléments dans les modèles.<br /><br /> Un *relation d’incorporation* indique que l’élément cible est détenu ou contenu par l’élément source et apparaît sous la forme d’un trait plein. Chaque élément dans un modèle doit être la cible d’une relation d’incorporation, afin que le modèle forme une arborescence. A *relation de référence* indique un lien entre les éléments de modèle général et s’affiche comme une ligne en pointillé. Tout élément peut avoir n’importe quel nombre de liens de référence.<br /><br /> Créer une relation en cliquant sur l’outil dans le **boîte à outils**, en cliquant sur la classe de domaine source, puis en cliquant sur la classe cible.|  
|Formes et connecteurs|Formes de spécifient comment les éléments de modèle doivent être affichées sur un diagramme DSL., connecteurs spécifient des lignes dans un diagramme DSL qui peut être utilisé pour afficher les relations.<br /><br /> Pour créer une forme ou un connecteur, faites glisser l’outil pour la **des éléments de diagramme** côté du diagramme.|  
|Mappages de formes|Mappage de forme apparaît comme une ligne sur le diagramme de modèle de domaine, liaison d’une forme à la classe de domaine qu’il affiche, ou d’un connecteur à la relation de domaine qui s’affiche.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des outils Domain-Specific Language](../modeling/overview-of-domain-specific-language-tools.md)   
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)
