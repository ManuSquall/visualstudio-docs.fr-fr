---
title: Propriétés des éléments UML utilisent des diagrammes de cas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b52afab80bc22c03dc5ff980b937cad53869f5db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444413"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Propriétés d'éléments sur des diagrammes de cas d'usage UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de cas d'usage UML, chaque élément possède des propriétés. Pour afficher les propriétés d’un élément, cliquez sur l’élément sur le diagramme ou dans **Explorateur de modèles UML** puis cliquez sur **propriétés**. Les propriétés s’affichent dans le **propriétés** fenêtre.  
  
> [!NOTE]
> Cette rubrique traite des propriétés d'éléments dans les diagrammes de cas d'usage UML. Pour plus d’informations sur la lecture des diagrammes d’activités UML, consultez [diagrammes de cas d’usage UML : Référence](../modeling/uml-use-case-diagrams-reference.md). Pour plus d’informations sur la façon de dessiner des diagrammes d’activités UML, consultez [diagrammes de cas d’usage UML : Les instructions](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propriétés des éléments  
  
|Propriété|Par défaut|Élément|Description|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nom par défaut|Tous|Identifie l'élément.|  
|**Nom qualifié**|Package :: Nom|Tous|Identifie l'élément de manière unique. A pour préfixe le nom qualifié du package qui le contient.|  
|**Éléments de travail**|{0} associé|Tous|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|  
|**Description**|(aucun)|Tous|Vous pouvez consigner des remarques générales concernant l'élément.|  
|**Color**|(valeur par défaut)|Tous|Couleur de la forme. Contrairement aux autres propriétés, il ne s'agit pas d'une propriété de l'élément affichée par la forme.|  
|**Chemin d’accès de l’image**|(aucun)|Acteur|Chemin d'accès d'une image qui doit être utilisée au lieu de l'icône d'acteur par défaut. L'icône doit être un fichier de ressources dans le projet Visual Studio.|  
|**Sujets**|(aucun)|Cas d'usage|Sous-système ou autre type qui possède le cas d'usage.<br /><br /> Vous pouvez le définir en plaçant le cas d'usage sur un sous-système dans le diagramme.|  
|**Visibilité**|Public|Cas d'usage, Acteur, Sous-système|**Public** : visible globalement.<br /><br /> **Package** : visible dans le package.|  
|**IsAbstract**|False|Cas d'usage, Acteur, Sous-système|Si la valeur est true, le type ne peut pas être instancié et constitue une base pour la spécialisation par d'autres définitions.|  
|**Is Indirectly Instantiated**|True|Sous-système|Le sous-système existe uniquement en tant qu'artefact de conception. Au moment de l'exécution, seuls ses éléments existent.|  
|**Lien hypertexte**|(aucun)|Artefact|Chemin d'accès de fichier ou URL du diagramme ou du document vers lequel l'artefact fournit un lien.|  
  
 Pour obtenir la liste des propriétés d’associations, voir [propriétés des associations dans UML des diagrammes de classes](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de cas d’usage UML : Référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammes de cas d’usage UML : Recommandations](../modeling/uml-use-case-diagrams-guidelines.md)
