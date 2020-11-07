---
title: Programmation de Visual Studio Tools pour Unity | Microsoft Docs
description: Consultez des exemples de programmation à l’aide de l’API Outils Visual Studio pour Unity (VSTU). Personnaliser les fichiers projet créés par VSTU. Partager le rappel de journal Unity avec VSTU.
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c98a3cdbcece87ad5e8fbe0e91ae76f677494477
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341665"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programmer Visual Studio Tools pour Unity
Dans cette section, vous trouverez des exemples de l'utilisation de l'API Visual Studio Tools pour Unity.

## <a name="examples"></a>Exemples
 Voici quelques exemples qui montrent comment vous pouvez utiliser les outils Visual Studio pour les API Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personnaliser les fichiers projet créés par VSTU
 Visual Studio Tools pour Unity fournit un rappel de type Unity pendant la génération du fichier projet. Pour savoir comment vous pouvez modifier le fichier projet chaque fois qu’il est régénéré, consultez [exemple : génération de fichier projet](./customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Partager le rappel de journal Unity avec VSTU
 Visual Studio Tools pour Unity enregistre un rappel de journal avec Unity pour pouvoir diffuser sa console vers Visual Studio. Si vos scripts de l'éditeur enregistrent également un rappel de journal avec Unity, le rappel VSTU peut interférer avec lui.  Pour savoir comment vous pouvez partager le rappel de journal Unity avec VSTU, consultez [exemple : rappel de journal](./share-the-unity-log-callback-with-vstu.md).
