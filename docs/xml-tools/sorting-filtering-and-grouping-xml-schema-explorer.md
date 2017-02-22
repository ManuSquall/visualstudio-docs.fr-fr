---
title: "Tri, filtrage et regroupement (Explorateur de sch&#233;mas XML) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Tri, filtrage et regroupement (Explorateur de sch&#233;mas XML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les options disponibles via le menu **Options de tri, de filtrage et de regroupement** dans la barre d'outils Explorateur de schémas XML.  
  
## Options de filtrage  
 Les options de filtrage suivantes sont disponibles.Par défaut, les options **Afficher les espaces de noms** et **Afficher les fichiers de schéma** sont sélectionnées.  
  
-   **Afficher les espaces de noms**.  
  
-   **Afficher les fichiers de schéma**.  
  
-   **Afficher les éléments de composition \(séquence\/choix\/tous\)**.  
  
## Options de tri  
 Les options de tri suivantes sont disponibles.La valeur par défaut est **Trier par type**.Les options Trier par ne s'appliquent pas aux fichiers et aux espaces de noms.  
  
-   **Trier par type**.  
  
-   **Trier par nom**.  
  
-   **Ordre du document**.  
  
### Trier par type  
 Lorsque l'option **Trier par type** est sélectionnée, les nœuds globaux sont triés dans l'ordre suivant.Les nœuds sont ensuite triés par ordre alphabétique dans chaque groupe.  
  
1.  Nœuds `import`.  
  
2.  Nœuds `include`.  
  
3.  Nœuds `redefine`.  
  
4.  Nœuds `attribute`.  
  
5.  Nœuds `attributeGroup`.  
  
6.  Nœuds `complexType`.  
  
7.  Nœuds `simpleType`.  
  
8.  Nœuds `element`.  
  
9. Nœuds `group`.  
  
### Trier par nom  
 Lorsque l'option **Trier par nom** est sélectionnée, les nœuds globaux sont triés dans l'ordre suivant :  
  
1.  Nœuds `import` \(par ordre alphabétique des espaces de noms\).  
  
2.  Nœuds `include` \(par ordre alphabétique des attributs `schemaLocation`\).  
  
3.  Nœuds `redefine` \(par ordre alphabétique des attributs `schemaLocation`\).  
  
4.  Autres nœuds globaux par ordre alphabétique.  
  
### Ordre du document  
 L'option **Ordre du document** est disponible lorsque l'option **Afficher les fichiers de schéma** est sélectionnée.Lorsque l'option **Ordre du document** est sélectionnée, les nœuds globaux s'affichent dans l'ordre dans lequel ils apparaissent dans le fichier de schéma.  
  
## Persistance des options de tri\/filtrage  
 Les options de tri, de filtrage et de regroupement sont enregistrées dans le Registre pour chaque utilisateur, indépendamment de la solution ou des fichiers ouverts lors de la modification des paramètres.