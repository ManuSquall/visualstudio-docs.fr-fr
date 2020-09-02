---
title: Start | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: df3ccda9730be02bafb7f7d069a26193a4528d1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778269"
---
# <a name="start"></a>Démarrer
L’option **Start** est une option de *VSPerfCmd.exe* qui initialise le profileur avec la méthode de profilage spécifiée.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Paramètres
 `Method` Doit correspondre à l’un des mots clés suivants :

- **TRACE** - Spécifie la méthode d’instrumentation.

- **SAMPLE** - Spécifie la méthode d’échantillonnage.

- **COVERAGE** - Spécifie la couverture du code.

- **CONCURRENCY** - Spécifie la méthode de résolution des conflits de ressources.

## <a name="required-options"></a>Options obligatoires
 L’option **Output** doit être spécifiée quand **Start** est spécifié sur la ligne de commande.

 **Sortie :** `filename` Spécifie le nom du fichier de sortie.

## <a name="exclusive-options"></a>Options exclusives
 Les options suivantes peuvent être utilisées seulement avec l’option **Start** sur une ligne de commande.

 **CrossSession**&#124;**CS** Active le profilage interprocessus. Les noms **CrossSession** et **CS** de l’option sont tous deux pris en charge.

 **Utilisateur :**[ `domain\` ] `username` active l’accès client au moniteur à partir du compte spécifié.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** spécifie un compteur de performances Windows à inclure en tant que marque dans le fichier de données de profilage. **AutoMark** spécifie l’intervalle en millisecondes entre les collectes du fichier de données.

## <a name="invalid-options"></a>Options non valides
 Les options suivantes ne peuvent pas être utilisées avec l’option **Start** sur une ligne de commande.

 **Status** **Status** s’applique aux processus profilés. Il répertorie les processus et les threads, ainsi que l’état de leur profil actuel (Activé/Désactivé). Par exemple, si un processus est arrêté, **Status** ne l’indique pas dans le rapport. **Status** indique que le processus est profilé ou non.

 **Shutdown**[**:** `Timeout` ] désactive le profileur.

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser l’option de **démarrage** *VSPerfCmd.exe* pour initialiser le profileur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
