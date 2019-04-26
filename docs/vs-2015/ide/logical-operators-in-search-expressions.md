---
title: Opérateurs logiques dans les expressions de recherche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30a33a434540fded8daab0628d0bd6dd7fb0ff38
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412268"
---
# <a name="logical-operators-in-search-expressions"></a>Opérateurs logiques dans les expressions de recherche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À l’aide des opérateurs logiques, vous pouvez affiner votre recherche de contenu en créant des expressions de recherche plus complexes. Comme le montre le tableau suivant, les opérateurs logiques spécifient comment plusieurs termes de recherche doivent être combinés dans une requête de recherche.  
  
> [!IMPORTANT]
> Vous devez entrer les opérateurs logiques tout en majuscules pour que le moteur de recherche puisse les reconnaître.  
  
|Pour rechercher|Utilisez|Exemple|Résultat|  
|-------------------|---------|-------------|------------|  
|Les deux termes dans la même rubrique|AND|dib AND palette|Rubriques qui contiennent « dib » et « palette ».|  
|L’un ou l’autre terme dans une rubrique|OR|trame OR vecteur|Rubriques qui contiennent « trame » ou « vecteur ».|  
|Premier terme sans le second terme dans la même rubrique|NOT|« système d’exploitation » NOT DOS|Rubriques qui contiennent « système d’exploitation » mais pas « DOS ».|  
|Les deux termes, proches dans une rubrique|NEAR|utilisateur NEAR noyau|Rubriques qui contiennent « utilisateur » à proximité de « noyau ».|  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de recherche en texte intégral](../ide/full-text-search-tips.md)   
 [Rechercher des informations](../ide/locate-information.md)
