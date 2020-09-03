---
title: Modules | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738348"
---
# <a name="modules"></a>Modules
En termes d’architecture du débogueur, un *module*:

- Est un conteneur physique de code, tel qu’un fichier exécutable ou une DLL.

- Peut recharger ses symboles et se décrire lui-même. Les descriptions de module s’affichent dans la fenêtre modules de l’IDE.

- Est représenté par une interface [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , créée par un moteur de débogage pour décrire le module.

## <a name="see-also"></a>Voir aussi
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
