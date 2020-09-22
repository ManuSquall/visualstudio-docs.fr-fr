---
title: Déboguer les exceptions ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 011094eed88245e3cd83b092a3f1b2e47bc77ae8
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852150"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Comment : déboguer des exceptions ASP.NET
Le débogage d’exceptions est une partie importante du développement d’une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fiable. Pour plus d’informations sur le débogage des exceptions, consultez [gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md).

 Pour déboguer des exceptions [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non gérées, vous devez vous assurer que le débogueur s’arrête pour elles. Le runtime [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a un gestionnaire d'exceptions de niveau supérieur. Par conséquent, le débogueur ne s'arrête jamais par défaut sur les exceptions non gérées. Pour arrêter le débogueur lorsqu’une exception est levée, vous devez sélectionner le paramètre **Arrêter lorsqu’une exception est : Levé** pour cette exception spécifique dans la boîte de dialogue **Exceptions**.

 Si vous avez activé Uniquement mon code, **arrêter lorsqu’une exception est : levée** n’entraîne pas l’arrêt immédiat du débogueur si une exception est levée dans une méthode .net ou un autre code système. En revanche, l'exécution continue jusqu'à ce que le débogueur atteigne du code du non-système, puisse elle s'arrête. Résultat : vous n'avez pas à parcourir le code de système lorsqu'une exception se produit.

 Uniquement mon code offre une autre option qui peut vous être encore plus utile : **Arrêter lorsqu’une exception est : Non géré par l’utilisateur**. Si vous affectez ce paramètre à une exception, le débogueur arrêtera l'exécution du code utilisateur, mais uniquement si l'exception n'est pas interceptée et gérée par le code utilisateur. Ce paramètre annule l'effet du gestionnaire d'exceptions [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de niveau supérieur, parce que ce gestionnaire se trouve dans du code non-utilisateur.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Activer le débogage des exceptions ASP.NET avec Uniquement mon code

1. Dans le menu **Déboguer**, cliquez sur **Exceptions**.

     La boîte de dialogue **Exceptions** s’affiche.

2. Sur la ligne **Exceptions du Common Language Runtime**, sélectionnez **Levé** ou **Non géré par l’utilisateur**.

     Pour pouvoir utiliser **Non géré par l’utilisateur**, vous devez activer **Uniquement mon code**.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Pour utiliser les meilleures pratiques pour la gestion des exceptions ASP.NET

- Placez des blocs `try ... catch` autour du code qui peut lever des exceptions que vous pouvez anticiper et que vous savez gérer. Par exemple, si l’application effectue des appels à un service web XML ou directement à un SQL Server, ce code doit se trouver dans des blocs **try ... catch**, car de nombreuses exceptions risquent de se produire.

## <a name="see-also"></a>Voir aussi
- [Déboguer des applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)