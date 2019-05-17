---
title: Mappages de version de package Roslyn pris en charge
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b2dd97b078923cfa3358d56e6316bfff654c4dd
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878239"
---
# <a name="net-compiler-platform-package-version-reference"></a>Référence de version de package .NET du compilateur plateforme

Le tableau suivant montre quelles [package de platform (Roslyn) du compilateur .NET](https://www.nuget.org/packages/Microsoft.Net.Compilers/) versions sont prises en charge pour les différentes versions de Visual Studio.

Par exemple, pour vous assurer que votre analyseur personnalisé fonctionne sur toutes les versions de Visual Studio 2017, il doit cibler la version 2.0 de Microsoft.Net.Compilers.

| Version du package Roslyn | Minimale prise en charge la version de Visual Studio |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 version 15.9 |
| 2.9.0 | Visual Studio 2017 version 15.8 |
| 2.8.2 | Visual Studio 2017 version 15.7 |
| 2.7.0 | Visual Studio 2017 version 15.6 |
| 2.6.1 | Visual Studio 2017 version 15.5 |
| 2.4.0 | Visual Studio 2017 version 15.4 |
| 2.3.2 | Visual Studio 2017 version 15.3 |
| 2.2.0 | Visual Studio 2017 version 15.2 |
| 2.1.0 | Visual Studio 2017 version 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 update 3 |
| 1.2.2 | Visual Studio 2015 update 2 |
| 1.1.1 | Visual Studio 2015 update 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> Pour les packages de Roslyn où la version de Visual Studio prises en charge minimale est une version de Visual Studio 2017, toutes les versions de Visual Studio 2019 sont également prises en charge, car ils étaient plus tard.

## <a name="see-also"></a>Voir aussi

- [SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
- [Prise en main des analyseurs de Roslyn](getting-started-with-roslyn-analyzers.md)