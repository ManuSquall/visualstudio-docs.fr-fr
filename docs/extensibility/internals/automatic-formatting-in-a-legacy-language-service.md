---
title: "La mise en forme automatique dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09ab8a948011cdc53516ec21f0d213852166956
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Mise en forme dans un Service de langage hérité automatique
Avec la mise en forme automatique, un service de langage insère automatiquement un extrait de code lorsqu’un utilisateur commence à taper une construction de code connus.  
  
## <a name="automatic-formatting-behavior"></a>Comportement de mise en forme automatique  
 Par exemple, lorsque vous tapez `if`, le service de langage insère automatiquement les accolades correspondantes, ou si vous appuyez sur la touche entrée, le service de langage force le point d’insertion sur la nouvelle ligne au niveau de retrait, selon que l’exemple précédent ligne ouvre une nouvelle étendue.  
  
 Le filtre de commande utilisé pour le reste du service de langage peut également être utilisé pour la mise en forme automatique. Vous pouvez également en surbrillance les accolades correspondantes en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)