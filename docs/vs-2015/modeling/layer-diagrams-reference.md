---
title: 'Diagrammes de couche : Référence | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c44ad4b225b3fd52f0e25369777b1a4f6df8c95e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248311"
---
# <a name="layer-diagrams-reference"></a>Diagrammes de couche : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser un *diagramme de couche* pour visualiser l’architecture de haut niveau et logique de votre système. Un diagramme de couche organise les artefacts physiques dans votre système en groupes logiques et abstraits appelés *couches*. Ces couches décrivent les tâches principales que les artefacts exécutent ou les principaux composants de votre système. Chaque couche peut également contenir des couches imbriquées qui décrivent des tâches plus détaillées.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Vous pouvez spécifier les dépendances prévues ou existantes entre des couches. Ces dépendances, représentées comme des flèches, indiquent quelles couches peuvent utiliser ou actuellement utiliser la fonctionnalité représentée par d'autres couches. En organisant votre système en couches qui décrivent des fonctions et des rôles distincts, un diagramme de couche peut simplifier la compréhension, la réutilisation et la maintenance de votre code.  
  
 Utilisez un diagramme de couche pour vous aider à effectuer les tâches suivantes :  
  
-   communiquer l'architecture logique existante ou prévue de votre système ;  
  
-   découvrir des conflits entre votre code existant et l'architecture prévue ;  
  
-   visualiser l'impact de modifications sur l'architecture prévue quand vous refactorisez, mettez à jour ou faites évoluer votre système ;  
  
-   renforcer l'architecture prévue pendant le développement et la maintenance de votre code en incluant la validation avec vos opérations de build et d'archivage.  
  
 Cette rubrique décrit les éléments que vous pouvez utiliser sur un diagramme de couche. Pour plus d’informations sur la façon de créer et dessiner des diagrammes de couche, consultez [diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md). Pour plus d’informations sur les modèles en couches, visitez le [Patterns & Practices site](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-layer-diagrams"></a>Lecture des diagrammes de couche  
 ![Éléments des diagrammes de couche](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")  
  
 Le tableau suivant décrit les éléments que vous pouvez utiliser sur un diagramme de couche.  
  
|**Forme**|**Élément**|**Description**|  
|---------------|-----------------|---------------------|  
|1|**Couche**|Groupe logique d'artefacts physiques dans votre système. Ces artefacts peuvent correspondre à des espaces de noms, des projets, des classes, des méthodes, etc.<br /><br /> Pour voir les artefacts qui sont liés à une couche, ouvrez le menu contextuel de la couche, puis choisissez **afficher les liens** pour ouvrir **Explorateur de couches**.<br /><br /> Pour plus d’informations, consultez [Explorateur de couches](#Explorer).<br /><br /> -   **Il est interdit de dépendances de Namespace** -Spécifie que les artefacts associés à cette couche ne peut pas dépendre d’espaces de noms spécifiés.<br />-   **Il est interdit d’espaces de noms** -Spécifie que les artefacts associés à cette couche ne doivent pas appartenir aux espaces de noms spécifiés.<br />-   **Required Namespaces** -Spécifie que les artefacts associés à cette couche doivent appartenir à un des espaces de noms spécifiés.|  
|2|**dépendance**|Indique qu'une couche peut utiliser les fonctionnalités d'une autre couche, mais pas l'inverse.<br /><br /> -   **Direction** -spécifie la direction de la dépendance.|  
|3|**Dépendance bidirectionnelle**|Indique qu'une couche peut utiliser les fonctionnalités d'une autre couche, et vice versa.<br /><br /> -   **Direction** -spécifie la direction de la dépendance.|  
|4|**Commentaire**|Permet d'ajouter des remarques générales au diagramme ou aux éléments du diagramme.|  
|5|**Lien de commentaire**|Permet de lier des commentaires aux éléments du diagramme.|  
  
##  <a name="Explorer"></a> Explorateur de couches  
 Vous pouvez lier chaque couche aux artefacts de votre solution, tels que des projets, des classes, des espaces de noms, des fichiers projet et d'autres parties de votre logiciel. Le nombre indiqué sur une couche représente le nombre d'artefacts liés à cette couche. Toutefois, quand vous lisez le nombre d'artefacts sur une couche, tenez compte des points suivants :  
  
-   Si une couche est liée à un artefact contenant d'autres artefacts, mais n'est pas directement liée à ces autres artefacts, le nombre représentera uniquement les artefacts auxquels elle est directement liée. Toutefois, les autres artefacts sont inclus dans l'analyse pendant la validation de couche.  
  
     Par exemple, si une couche est liée à un espace de noms unique, le nombre d'artefacts liés est égal à 1, même si l'espace de noms contient des classes. Si la couche a également des liens vers chaque classe de l'espace de noms, le nombre comprendra les classes liées.  
  
-   Si une couche contient d'autres couches liées à des artefacts, la couche du conteneur est également liée à ces artefacts, même si le nombre indiqué sur la couche du conteneur ne comprend pas ces artefacts.  
  
 Pour plus d'informations sur la liaison des couches et des artefacts, consultez :  
  
-   [Diagrammes de couche : recommandations](../modeling/layer-diagrams-guidelines.md)  
  
-   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Pour examiner les artefacts liés  
  
-   Sur le diagramme de couche, ouvrez le menu contextuel pour une ou plusieurs couches, puis choisissez **afficher les liens**.  
  
     **Explorateur de couches** s’ouvre et affiche les artefacts liés aux couches sélectionnées. **Explorateur de couches** a une colonne qui affiche chacune des propriétés des liens d’artefact.  
  
    > [!NOTE]
    >  Si vous ne voyez pas toutes ces propriétés, développez le **Explorateur de couches** fenêtre.  
  
    |**Colonne dans l’Explorateur de couches**|**Description**|  
    |----------------------------------|---------------------|  
    |**Catégories**|Genre d'artefact, tel qu'une classe, un espace de noms, un fichier source, etc.|  
    |**Couche**|Couche liée à l'artefact.|  
    |**Prend en charge la Validation**|Si **True**, puis le processus de validation de couche peut vérifier que le projet est conforme aux dépendances vers ou à partir de cet élément.<br /><br /> Si **False**, puis le lien ne participe pas le processus de validation de couche.<br /><br /> Pour plus d’informations, consultez [diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificateur**|Référence à l'artefact lié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)



