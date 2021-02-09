---
title: Modules | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un module dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926322"
---
# <a name="modules"></a>Modules
En termes d’architecture du débogueur, un *module*:

- Est un conteneur physique de code, tel qu’un fichier exécutable ou une DLL.

- Peut recharger ses symboles et se décrire lui-même. Les descriptions de module s’affichent dans la fenêtre modules de l’IDE.

- Est représenté par une interface [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , créée par un moteur de débogage pour décrire le module.

## <a name="see-also"></a>Voir aussi
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
