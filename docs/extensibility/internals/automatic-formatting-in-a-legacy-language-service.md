---
title: Mise en forme automatique dans un service de langage hérité | Microsoft Docs
description: En savoir plus sur la mise en forme automatique dans un service de langage hérité, qui insère automatiquement un extrait de code lorsque vous commencez à taper une construction de code connue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de54f43ca8abc7547609882647e014cb3695da33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906052"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Mise en forme automatique dans un service de langage hérité
Avec la mise en forme automatique, un service de langage insère automatiquement un extrait de code lorsqu’un utilisateur commence à taper une construction de code connue.

## <a name="automatic-formatting-behavior"></a>Comportement de mise en forme automatique
 Par exemple, lorsque vous tapez *si*, le service de langage insère automatiquement des accolades correspondantes, ou si vous appuyez sur la touche entrée, le service de langage force le point d’insertion sur la nouvelle ligne au niveau de retrait approprié, selon que la ligne précédente ouvre ou non une nouvelle étendue.

 Le filtre de commande utilisé pour le reste du service de langage peut également être utilisé pour la mise en forme automatique. Vous pouvez également mettre en surbrillance les accolades correspondantes en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Voir aussi
- [Développer un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
