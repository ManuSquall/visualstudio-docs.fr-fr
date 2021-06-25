---
title: Modules | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un module dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03a3ad588b0a2e0f3aa6f04ddeb742ab66064bc9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902603"
---
# <a name="modules"></a>Modules
En termes d’architecture du débogueur, un *module*:

- Est un conteneur physique de code, tel qu’un fichier exécutable ou une DLL.

- Peut recharger ses symboles et se décrire lui-même. Les descriptions de module s’affichent dans la fenêtre modules de l’IDE.

- Est représenté par une interface [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , créée par un moteur de débogage pour décrire le module.

## <a name="see-also"></a>Voir aussi
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
