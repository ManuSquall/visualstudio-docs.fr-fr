---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed60fb5262a6af07966ff974b8535ae299f3fc51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861411"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
Définit par sa présence si une instance par défaut de la classe de [classe vsgdbg,](vsgdbg-class.md) , qui fournit l’interface de capture par programmation, est fournie.

## <a name="syntax"></a>Syntaxe

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>Valeur
 Symbole de préprocesseur dont la présence ou l’absence détermine si une instance par défaut de la `VsgDbg` classe est fournie. Si ce symbole est défini, aucune instance par défaut de la `VsgDbg` classe n’est fournie ; sinon, une instance par défaut est fournie et initialisée avant l’exécution de votre programme.

 L’interface de capture par programmation est fournie via un pointeur qui a une portée globale, `g_pVsgDbg` .

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>Remarques
 L’instance par défaut est souvent suffisante, mais pour utiliser l’interface de capture par programmation à l’intérieur d’une DLL lorsque l’appareil D3D a été créé en dehors de cette DLL, vous devez créer et gérer votre propre instance de la `VsgDbg` classe. Si vous gérez votre propre interface avec l’API de capture par programmation de cette manière, désactivez l’instance par défaut en définissant `VSG_NODEFAULT_INSTANCE` pour éviter une surcharge.

 Si l’instance par défaut n’est pas désactivée, elle est automatiquement initialisée avant l’exécution de votre programme et est automatiquement détruite à la fin de votre programme. Vous n’avez pas besoin d’initialiser ou d’initialiser cette instance explicitement.

 Pour désactiver l’instance par défaut, vous devez définir `VSG_NODEFAULT_INSTANCE` avant `vsgcapture.h` d’inclure dans votre programme.

## <a name="example"></a>Exemple
 Cet exemple montre comment désactiver l’instance par défaut :

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
