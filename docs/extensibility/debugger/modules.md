---
title: Modules Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738348"
---
# <a name="modules"></a>Modules
En termes d’architecture débbugger, un *module*:

- Est un conteneur physique de code, comme un fichier exécutable ou un DLL.

- Peut recharger ses symboles et se décrire lui-même. Les descriptions du module sont affichées dans la fenêtre Modules de l’IDE.

- Est représenté par une interface [IDebugModule2,](../../extensibility/debugger/reference/idebugmodule2.md) créée par un moteur de débogé pour décrire le module.

## <a name="see-also"></a>Voir aussi
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
