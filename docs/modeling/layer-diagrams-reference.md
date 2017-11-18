---
title: "Schémas de dépendance : Référence | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: "33"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: ce4a203fd0843fd6b15bfbf85019e85032defbd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="dependency-diagrams-reference"></a>Diagrammes de dépendance : référence
Dans Visual Studio, vous pouvez utiliser un *diagramme de dépendances* pour visualiser l’architecture de haut niveau, la logique de votre système. Un diagramme de dépendances organise les artefacts physiques dans votre système en groupes logiques et abstraits appelés *couches*. Ces couches décrivent les tâches principales que les artefacts exécutent ou les principaux composants de votre système. Chaque couche peut également contenir des couches imbriquées qui décrivent des tâches plus détaillées.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Vous pouvez spécifier les dépendances prévues ou existantes entre des couches. Ces dépendances, représentées comme des flèches, indiquent quelles couches peuvent utiliser ou actuellement utiliser la fonctionnalité représentée par d'autres couches. En organisant votre système en couches qui décrivent les fonctions et les rôles distincts, un diagramme de dépendances peut aider à rendre plus facile à comprendre, réutiliser et gérer votre code.  
  
 Utilisez un diagramme de dépendances pour vous aider à effectuer les tâches suivantes :  
  
-   communiquer l'architecture logique existante ou prévue de votre système ;  
  
-   découvrir des conflits entre votre code existant et l'architecture prévue ;  
  
-   visualiser l'impact de modifications sur l'architecture prévue quand vous refactorisez, mettez à jour ou faites évoluer votre système ;  
  
-   renforcer l'architecture prévue pendant le développement et la maintenance de votre code en incluant la validation avec vos opérations de build et d'archivage.  
  
 Cette rubrique décrit les éléments que vous pouvez utiliser sur un diagramme de dépendances. Pour plus d’informations sur la création et dessiner des diagrammes de dépendance, consultez [des diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md). Pour plus d’informations sur les modèles en couches, visitez le [site Patterns & Practices](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Lecture des diagrammes de dépendance  
 ![Éléments des diagrammes de dépendance](../modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 Le tableau suivant décrit les éléments que vous pouvez utiliser sur un diagramme de dépendances.  
  
|**Forme**|**Élément**|**Description**|  
|---------------|-----------------|---------------------|  
|1|**Couche**|Groupe logique d'artefacts physiques dans votre système. Ces artefacts peuvent correspondre à des espaces de noms, des projets, des classes, des méthodes, etc.<br /><br /> Pour voir les artefacts qui sont liés à une couche, ouvrez le menu contextuel de la couche, puis choisissez **afficher les liens** pour ouvrir **Explorateur de couches**.<br /><br /> Pour plus d’informations, consultez [Explorateur de couches](#Explorer).<br /><br /> -   **Il est interdit de dépendances de Namespace** -Spécifie que les artefacts associés à cette couche ne peuvent pas dépendre d’espaces de noms spécifiés.<br />-   **Il est interdit d’espaces de noms** -Spécifie que les artefacts associés à cette couche ne doivent pas appartenir aux espaces de noms spécifiés.<br />-   **Requis des espaces de noms** -Spécifie que les artefacts associés à cette couche doivent appartenir à un des espaces de noms spécifiés.|  
|2|**Dépendance**|Indique qu'une couche peut utiliser les fonctionnalités d'une autre couche, mais pas l'inverse.<br /><br /> -   **Direction** -spécifie la direction de la dépendance.|  
|3|**Dépendance bidirectionnelle**|Indique qu'une couche peut utiliser les fonctionnalités d'une autre couche, et vice versa.<br /><br /> -   **Direction** -spécifie la direction de la dépendance.|  
|4|**Commentaire**|Permet d'ajouter des remarques générales au diagramme ou aux éléments du diagramme.|  
|5|**Lien de commentaire**|Permet de lier des commentaires aux éléments du diagramme.|  
  
##  <a name="Explorer"></a>Explorateur de couches  
 Vous pouvez lier chaque couche aux artefacts de votre solution, tels que des projets, des classes, des espaces de noms, des fichiers projet et d'autres parties de votre logiciel. Le nombre indiqué sur une couche représente le nombre d'artefacts liés à cette couche. Toutefois, quand vous lisez le nombre d'artefacts sur une couche, tenez compte des points suivants :  
  
-   Si une couche est liée à un artefact contenant d'autres artefacts, mais n'est pas directement liée à ces autres artefacts, le nombre représentera uniquement les artefacts auxquels elle est directement liée. Toutefois, les autres artefacts sont inclus dans l'analyse pendant la validation de couche.  
  
     Par exemple, si une couche est liée à un espace de noms unique, le nombre d'artefacts liés est égal à 1, même si l'espace de noms contient des classes. Si la couche a également des liens vers chaque classe de l'espace de noms, le nombre comprendra les classes liées.  
  
-   Si une couche contient d'autres couches liées à des artefacts, la couche du conteneur est également liée à ces artefacts, même si le nombre indiqué sur la couche du conteneur ne comprend pas ces artefacts.  
  
 Pour plus d'informations sur la liaison des couches et des artefacts, consultez :  
  
-   [Diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md)  
  
-   [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Pour examiner les artefacts liés  
  
-   Dans le diagramme de la dépendance, ouvrez le menu contextuel pour une ou plusieurs couches, puis choisissez **afficher les liens**.  
  
     **Explorateur de couches** s’ouvre et affiche les artefacts liés aux couches sélectionnées. **Explorateur de couches** a une colonne qui affiche chacune des propriétés des liens d’artefact.  
  
    > [!NOTE]
    >  Si vous ne voyez pas toutes ces propriétés, développez le **Explorateur de couches** fenêtre.  
  
    |**Colonne dans l’Explorateur de couches**|**Description**|  
    |----------------------------------|---------------------|  
    |**Catégories**|Genre d'artefact, tel qu'une classe, un espace de noms, un fichier source, etc.|  
    |**Couche**|Couche liée à l'artefact.|  
    |**Prend en charge la Validation**|Si **True**, puis le processus de validation de couche peut vérifier que le projet est conforme aux dépendances vers ou à partir de cet élément.<br /><br /> Si **False**, puis le lien ne participe pas le processus de validation de couche.<br /><br /> Pour plus d’informations, consultez [des diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificateur**|Référence à l'artefact lié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)
