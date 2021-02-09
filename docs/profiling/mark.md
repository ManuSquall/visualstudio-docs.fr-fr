---
title: Mark | Microsoft Docs
description: Découvrez comment l’option marque de VSPerfCmd.exe insère les informations spécifiées dans le fichier de données de profilage.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 33a343be010a5bf9cc0d9ba3e4251d92fd720656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917813"
---
# <a name="mark"></a>Marque
L’option *VSPerfCmd.exe* **marque** insère les informations spécifiées dans le fichier de données de profilage. Une marque peut apparaître dans un rapport VSPerfReport distinct ou dans la vue Rapport de marques de l’interface utilisateur du profileur. L’option **Mark** peut être utilisée pour spécifier des points de début et fin dans les filtres des rapports et des vues.

 L’option **Mark** doit être la seule option spécifiée sur la ligne de commande.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Paramètres
 `MarkID` Entier défini par l’utilisateur, qui est listé en tant qu’ID de marque dans les vues et les rapports du profileur. `MarkID` ne doit pas nécessairement être unique.

 `MarkName` (Facultatif) Chaîne définie par l’utilisateur, qui est listée en tant que nom de marque dans les vues et les rapports du profileur. Si `MarkName` n’est pas spécifié, le champ Nom de marque de la liste des marques est vide. Placez entre guillemets les chaînes qui contiennent des espaces ou des barres obliques (« / »).

## <a name="example"></a>Exemple
 Cet exemple insère une marque avec l’ID 123 et le nom de marque « TestMark ».

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
