---
title: La mise en forme automatique dans un Service de langage hérité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19c36f5a31c6d3ed7284922bc830ea4925da5833
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246725"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Mise en forme automatique dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avec la mise en forme automatique, un service de langage insère automatiquement un extrait de code lorsqu’un utilisateur commence à taper une construction de code connu.  
  
## <a name="automatic-formatting-behavior"></a>Comportement de mise en forme automatique  
 Par exemple, quand vous tapez `if`, le service de langage insère automatiquement les accolades correspondantes, ou si vous appuyez sur la touche entrée, le service de langage force le point d’insertion sur la nouvelle ligne au niveau de retrait, selon que l’exemple précédent ligne ouvre une nouvelle étendue.  
  
 Le filtre de commande utilisé pour le reste du service de langage peut également être utilisé pour la mise en forme automatique. Vous pouvez également sélectionner des accolades correspondantes en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)

