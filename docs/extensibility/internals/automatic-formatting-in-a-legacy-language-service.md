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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651cecb20604069c6e8ccc5a5c7b983ab43d7384
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190055"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Mise en forme automatique dans un service de langage hérité
Avec la mise en forme automatique, un service de langage insère automatiquement un extrait de code lorsqu’un utilisateur commence à taper une construction de code connue.

## <a name="automatic-formatting-behavior"></a>Comportement de mise en forme automatique
 Par exemple, lorsque vous tapez *si*, le service de langage insère automatiquement des accolades correspondantes, ou si vous appuyez sur la touche entrée, le service de langage force le point d’insertion sur la nouvelle ligne au niveau de retrait approprié, selon que la ligne précédente ouvre ou non une nouvelle étendue.

 Le filtre de commande utilisé pour le reste du service de langage peut également être utilisé pour la mise en forme automatique. Vous pouvez également mettre en surbrillance les accolades correspondantes en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Voir aussi
- [Développer un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
