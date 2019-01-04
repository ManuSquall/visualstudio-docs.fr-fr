---
title: La mise en forme automatique dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 89345c7cd466211292a21ec4ca99276ebf95d67a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873546"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Mise en forme dans un service de langage hérité automatique
Avec la mise en forme automatique, un service de langage insère automatiquement un extrait de code lorsqu’un utilisateur commence à taper une construction de code connu.  
  
## <a name="automatic-formatting-behavior"></a>Comportement de mise en forme automatique  
 Par exemple, quand vous tapez *si*, le service de langage insère automatiquement les accolades correspondantes, ou si vous appuyez sur la touche entrée, le service de langage force le point d’insertion sur la nouvelle ligne au niveau de retrait, en fonction de Indique si la ligne précédente ouvre une nouvelle étendue.  
  
 Le filtre de commande utilisé pour le reste du service de langage peut également être utilisé pour la mise en forme automatique. Vous pouvez également sélectionner des accolades correspondantes en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)