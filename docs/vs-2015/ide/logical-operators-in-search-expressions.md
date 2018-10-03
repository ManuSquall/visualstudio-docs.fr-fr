---
title: Opérateurs logiques dans les expressions de recherche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494612"
---
# <a name="logical-operators-in-search-expressions"></a>Opérateurs logiques dans les expressions de recherche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [opérateurs logiques dans les Expressions de recherche](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions).  
  
À l’aide des opérateurs logiques, vous pouvez affiner votre recherche de contenu en créant des expressions de recherche plus complexes. Comme le montre le tableau suivant, les opérateurs logiques spécifient comment plusieurs termes de recherche doivent être combinés dans une requête de recherche.  
  
> [!IMPORTANT]
>  Vous devez entrer les opérateurs logiques tout en majuscules pour que le moteur de recherche puisse les reconnaître.  
  
|Pour rechercher|Utilisez|Exemple|Résultat|  
|-------------------|---------|-------------|------------|  
|Les deux termes dans la même rubrique|AND|dib AND palette|Rubriques qui contiennent « dib » et « palette ».|  
|L’un ou l’autre terme dans une rubrique|OR|trame OR vecteur|Rubriques qui contiennent « trame » ou « vecteur ».|  
|Premier terme sans le second terme dans la même rubrique|NOT|« système d’exploitation » NOT DOS|Rubriques qui contiennent « système d’exploitation » mais pas « DOS ».|  
|Les deux termes, proches dans une rubrique|NEAR|utilisateur NEAR noyau|Rubriques qui contiennent « utilisateur » à proximité de « noyau ».|  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de recherche en texte intégral](../ide/full-text-search-tips.md)   
 [Rechercher des informations](../ide/locate-information.md)



