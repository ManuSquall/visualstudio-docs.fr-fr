---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43affa6db83d34d18a3f485a88f41ccde5d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804410"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit par sa présence si une instance par défaut de la [vsgdbg, classe](../debugger/vsgdbg-class.md) classe, qui fournit l’interface de capture par programmation — est fourni.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Value  
 Un préprocesseur qui symbole par sa présence ou absence détermine si une instance par défaut de la `VsgDbg` classe est fournie. Si ce symbole est défini, puis aucune instance par défaut de la `VsgDbg` classe est fournie ; sinon, une instance par défaut est fournie et initialisée avant l’exécution de votre programme.  
  
 L’interface de capture par programmation est fournie via un pointeur qui a une portée globale, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Notes  
 L’instance par défaut est souvent suffisante, mais pour utiliser l’interface de capture par programmation à l’intérieur d’une DLL lors de l’appareil D3D a été créé en dehors de cette DLL, vous devez créer et gérer votre propre instance de la `VsgDbg` classe. Si vous gérez votre propre interface à l’API de capture par programmation de cette façon, désactivez l’instance par défaut en définissant `VSG_NODEFAULT_INSTANCE` afin d’éviter la surcharge.  
  
 Si l’instance par défaut n’est pas désactivé, il est automatiquement initialisé avant l’exécution de votre programme et est automatiquement détruit lorsque votre programme se termine. Il est inutile d’initialiser ou annuler explicitement l’initialisation de cette instance.  
  
 Pour désactiver l’instance par défaut, vous devez définir `VSG_NODEFAULT_INSTANCE` avant d’inclure `vsgcapture.h` dans votre programme.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment désactiver l’instance par défaut :  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```



