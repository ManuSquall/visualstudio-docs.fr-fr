---
title: Formatage automatique dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709976"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatage automatique dans un service linguistique hérité
Avec le formatage automatique, un service linguistique insère automatiquement un extrait de code lorsqu’un utilisateur commence à taper une construction de code connue.

## <a name="automatic-formatting-behavior"></a>Comportement de formatage automatique
 Par exemple, lorsque vous tapez *si,* le service linguistique insère automatiquement les accolades assorties, ou si vous appuyez sur la clé ENTER, le service linguistique force le point d’insertion sur la nouvelle ligne au niveau d’indent approprié, selon que la ligne précédente ouvre une nouvelle portée.

 Le filtre de commande utilisé pour le reste du service linguistique peut également être utilisé pour le formatage automatique. Vous pouvez également mettre en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>évidence les accolades assorties en appelant .

## <a name="see-also"></a>Voir aussi
- [Développer un service linguistique hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
