---
title: User (VSPerfCmd) | Microsoft Docs
description: Découvrez comment l’option utilisateur spécifie le domaine et le nom d’utilisateur du compte propriétaire du processus profilé.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbb5490ff9281a7379d74209da15a3a39595bc09
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721162"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
L’option **User** spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est listé dans la colonne nom d’utilisateur sous l’onglet **processus** du gestionnaire des tâches de Windows.

 Vous pouvez spécifier l’option **User** seulement sur une ligne de commande qui contient aussi l’option **Start**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Paramètres
 `Domain` Nom du domaine de l’utilisateur.

 `UserName` Nom de l’utilisateur.

## <a name="required-options"></a>Options obligatoires
 L’option **User** peut être utilisée seulement avec l’option **Start**.

 **Démarrer :** `Method` Initialise le profileur avec la méthode de profilage spécifiée.

## <a name="example"></a>Exemples
 L’exemple suivant montre l’utilisation de l’option **User**.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
