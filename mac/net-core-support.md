---
title: Support de .NET Core
description: Ce document décrit la prise en charge des versions .NET Core dans Visual Studio pour Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: a04d15fc2fc768c2d6896396df5dc0f134d1720b
ms.sourcegitcommit: 67f3bdeee583a4fb41cacc7f38839a737bfecc6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2021
ms.locfileid: "105735523"
---
# <a name="net-core-support"></a>Support de .NET Core

Le tableau suivant décrit les versions .NET Core prises en charge par les versions stables et les préversions de Visual Studio pour Mac :

| Version du kit SDK .NET Core |Visual Studio pour Mac 8,1 | Visual Studio pour Mac 8,2 | Visual Studio pour Mac 8,3 | Visual Studio pour Mac 8,4 | Visual Studio pour Mac 8,5 | Visual Studio pour Mac 8,6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|5.0 | | | | | |✔︎|

> [!IMPORTANT]
> Les versions préliminaires des kit SDK .NET Core ne sont pas prises en charge ; Effectuez une mise à jour vers la version finale. Lors de l’installation de Visual Studio pour Mac 8,4, la version finale de .NET Core v 3.1 sera installée.

> [!IMPORTANT]
> Si vous utilisiez précédemment .NET Core v2.2.1xx avec Visual Studio pour Mac 8.0, vous devez manuellement effectuer une mise à jour vers une version prise en charge de .NET Core, comme indiqué dans le tableau ci-dessous. Nous vous recommandons d’utiliser [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) ou [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2)

* .NET Core v 3.1 est installé par défaut pour 8,4, 8,5 et 8,6.
* .NET Core v 3.0 est installé par défaut pour 8,3.
* .NET Core v2.1.701 (v2.1.700 pour 8.1) est installé par défaut avec le programme d’installation.
* Pour télécharger d’autres versions de .NET Core, visitez la [page dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* Lors de l’utilisation de .NET Core 3,0, C# version 8 sera utilisé par défaut. C# 7,3 est la valeur par défaut lors de l’utilisation de .NET Core 2. x. Pour plus d’informations, consultez contrôle de [version du langage C#](/dotnet/csharp/language-reference/configure-language-version) .
* Pour plus d’informations sur l’installation d’une préversion de Visual Studio pour Mac, consultez le guide [Installer une préversion](./install-preview.md).