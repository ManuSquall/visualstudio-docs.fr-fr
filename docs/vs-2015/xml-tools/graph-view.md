---
title: Vue graphique | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca48fecf68ad9ecd1db6dc61acbf168a0a1c0f14
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298530"
---
# <a name="graph-view"></a>Vue Graphique
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La vue du graphique fournit une représentation graphique des nœuds de schéma globaux et des relations entre les nœuds. Notez que la vue du graphique ne vous permet pas de modifier la disposition du jeu de schémas sur l'aire de conception. La vue du graphique comprend également la barre d'outils Concepteur de schémas XML et la barre de fil d'Ariane (breadcrumb).  
  
 L'image suivante montre la vue du graphique avec six nœuds globaux sur son aire de conception.  
  
 ![Vue graphique du Concepteur de schémas XML](../xml-tools/media/xsddesigner-graphview.gif "XSDDesigner_GraphView")  
  
## <a name="design-surface"></a>Aire de conception  
 L’aire de conception de la vue du graphique affiche le contenu de la [espace de travail Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md). Si l'espace de travail contient des nœuds globaux du jeu de schémas, les nœuds sont représentés sur l'aire de conception de la vue du graphique et des flèches sont dessinées entre les nœuds qui ont des relations.  
  
 Le fait de double-cliquer sur un nœud dans la vue du graphique affiche l'Éditeur XML.  
  
 Pour supprimer des nœuds sélectionnés de l'espace de travail, utilisez la barre d'outils Concepteur XSD ou la touche Suppr.  
  
 Si l'aire de conception est vide, l'Éditeur XML, l'Explorateur de schémas XML et le filigrane sont affichés. Le *filigrane* est une liste de liens vers toutes les vues du concepteur XSD.  
  
 ![Concepteur XSD ; Vue graphique](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")  
  
 Si le jeu de schémas comporte des erreurs, le texte suivant est affiché à la fin de la liste : « Utilisez la liste d'erreurs pour afficher et résoudre les erreurs dans le jeu ».  
  
## <a name="breadcrumb-bar"></a>Barre de fil d'Ariane (breadcrumb)  
 La barre de fil d'Ariane (breadcrumb) en bas de la vue du graphique indique l'emplacement du nœud sélectionné dans le jeu de schémas. Si plusieurs éléments sont sélectionnés, la barre de fil d'Ariane (breadcrumb) est vide.  
  
## <a name="context-menu"></a>Menu contextuel  
 Le tableau décrit les options disponibles pour tous les nœuds sur l'aire de conception de la vue du graphique.  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|  
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique (grisée).|  
|**Générer un exemple de XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|  
|**Effacer l’espace de travail**|Efface l'espace de travail et l'aire de conception.|  
|**Supprimer à partir de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|  
|**Supprimer toutes les valeurs sauf la sélection à partir de l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|  
|**Exporter le diagramme en tant qu’Image...**|Enregistre l’aire de conception dans un fichier XPS.|  
|**Sélectionner tout**|Sélectionne tous les nœuds sur l'aire de conception.|  
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML. L'élément sélectionné dans l'Explorateur de schémas XML est également sélectionné dans l'Éditeur XML.|  
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|  
  
 En plus des options communes décrites ci-dessus, le menu contextuel pour les éléments globaux comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Ajoutez la définition de Type**|Ajoute le type de base au diagramme.|  
|**Ajouter toutes les références**|Ajoute tous les nœuds qui font référence à l'élément et dessine des flèches pour indiquer les relations entre eux.|  
|**Ajouter des membres du groupe de Substitution**|Ajoute tous les membres du groupe de substitution. Cette option s'affiche dans la vue si l'élément est l'en-tête ou membre d'un groupe de substitution.|  
|**Générer un exemple de XML**|Génère un exemple de fichier XML pour l'élément global.|  
  
 En plus des options communes décrites ci-dessus, le menu contextuel pour les types simples et complexes globaux comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Ajouter le Type de Base**|Si le type sélectionné est dérivé d'un type global, ajoute le type de base du type sélectionné.|  
|**Ajouter toutes les références**|Ajoute toutes les références du type sélectionné. Ceci inclut les éléments et les attributs du type sélectionné, ainsi que les types dérivés du type sélectionné.|  
|**Ajouter tous les Types dérivés**|Ajoute tous les types qui sont directement et indirectement dérivés du type sélectionné.|  
|**Ajouter tous les ancêtres**|Ajoute tous les types parents (de base).|  
  
 En plus des options communes décrites ci-dessus, le menu contextuel pour les groupes globaux et les groupes d'attributs comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Ajouter toutes les références**|Ajoute tous les nœuds qui font référence au groupe et dessine des flèches pour indiquer les relations entre eux.|  
|**Ajouter tous les membres**|Ajoute tous les membres du groupe et dessine des flèches pour indiquer les relations entre eux.|  
  
 En plus des options communes décrites ci-dessus, le menu contextuel pour les attributs globaux comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Ajouter toutes les références**|Ajoute tous les nœuds qui font référence au groupe et dessine des flèches pour indiquer les relations entre eux.|  
  
## <a name="properties-window"></a>Propriétés (fenêtre)  
 Utilisez le menu contextuel pour ouvrir la **propriétés** fenêtre. Par défaut, le **propriétés** fenêtre apparaît dans le coin inférieur droit de Visual Studio. Lorsque vous cliquez sur un nœud qui est affiché dans la vue de modèle de contenu, les propriétés de ce nœud seront affichera dans le **propriétés** fenêtre.  
  
## <a name="xsd-toolbar"></a>Barre d'outils XSD  
 Les boutons suivants de la barre d'outils XSD sont activés lorsque la vue du graphique est active.  
  
 ![Barre d’outils de Concepteur de schémas XML](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher la vue de départ**|Bascule vers le [démarrer l’affichage](../xml-tools/start-view.md). Cette vue est accessible en utilisant le raccourci clavier : **CTRL + 1**.|  
|**Afficher la vue de modèle de contenu**|Bascule vers le [vue du modèle de contenu](../xml-tools/content-model-view.md). Cette vue est accessible en utilisant le raccourci clavier : **CTRL + 2**.|  
|**Afficher la vue du graphique**|Bascule vers le [vue graphique](../xml-tools/graph-view.md). Cette vue est accessible en utilisant le raccourci clavier : **CTRL + 3**.|  
|**Effacer l’espace de travail**|Efface l'espace de travail et l'aire de conception.|  
|**Supprimer à partir de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|  
|**Supprimer toutes les valeurs sauf la sélection à partir de l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception. Cette option est activée dans la vue de modèle de contenu et dans la vue du graphique.|  
|**Gauche à droite**|Modifie la disposition de la vue du graphique pour représenter hiérarchiquement les nœuds de gauche à droite. Cette option est accessible en utilisant le raccourci clavier : **Alt + flèche droite**.|  
|**De droite à gauche**|Modifie la disposition de la vue du graphique pour représenter hiérarchiquement les nœuds de droite à gauche. Cette option est accessible en utilisant le raccourci clavier : **Alt + flèche gauche**.|  
|**Haut en bas**|Modifie la disposition de la vue du graphique pour représenter hiérarchiquement les nœuds de haut en bas. Cette option est accessible en utilisant le raccourci clavier : **Alt + flèche vers le bas**.|  
|**Bas en haut**|Modifie la disposition de la vue du graphique pour représenter hiérarchiquement les nœuds de bas en haut. Cette option est accessible en utilisant le raccourci clavier : **Alt + flèche haut**.|  
  
## <a name="panscroll"></a>Panoramique/Défilement  
 Vous pouvez afficher un panoramique de l'aire de conception en utilisant les barres de défilement ou en maintenant la touche Ctrl enfoncée pendant que vous cliquez et faites glisser la souris. Lorsque vous affichez un panoramique de l'aire de conception en cliquant et en faisant glisser la souris, le curseur se transforme en cercle contenant quatre flèches qui pointent dans quatre directions.  
  
## <a name="undoredo"></a>Annuler/Rétablir  
 La fonction d'annulation/de rétablissement est activée dans la vue du graphique pour les actions suivantes :  
  
-   Ajout d'un nœud unique par glisser-déplacer.  
  
-   Ajout de plusieurs nœuds de la fenêtre des résultats de la recherche dans des requêtes de l'Explorateur de schémas ou de la vue de départ.  
  
-   Suppression d'un ou plusieurs nœuds.  
  
## <a name="zoom"></a>Zoom  
 Le zoom est disponible dans le coin inférieur droit de la vue du graphique.  
  
 Le zoom peut être contrôlé des façons suivantes :  
  
-   En maintenant la touche Ctrl enfoncée et en tournant la roulette de la souris lorsque la souris pointe sur la surface de la vue du graphique.  
  
-   En utilisant le contrôle Slider. Le curseur affiche le niveau de zoom actuel.  
  
 Le curseur Zoom est opaque lorsque vous le sélectionnez, pointez sur celui-ci ou utilisez Ctrl avec la roulette de la souris pour effectuer un zoom ; dans tous les autres cas, il est transparent.  
  
## <a name="xml-editor-integration"></a>Intégration de l'Éditeur XML  
 Vous pouvez basculer entre la vue du graphique et l'Éditeur XML en cliquant sur un nœud et en utilisant le menu contextuel Afficher le code.  
  
 Si vous apportez des modifications au jeu de schémas dans l’Éditeur XML, les modifications sont synchronisées dans la vue du graphique. Pour plus d’informations, consultez [intégration avec l’éditeur XML](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Aire de conception](../xml-tools/xml-schema-designer-workspace.md)



