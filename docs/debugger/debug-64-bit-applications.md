---
title: Déboguer des applications 64 bits | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 849862f98fb90cdd742e1794ecb57c35a9aaca73
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745579"
---
# <a name="debug-64-bit-applications"></a>Déboguer des applications 64 bits
Vous pouvez déboguer une application 64 bits qui s'exécute sur l'ordinateur local ou sur un ordinateur distant.

 Pour déboguer une application 64 bits qui s’exécute sur un ordinateur distant, consultez [Remote Debugging](../debugger/remote-debugging.md).

 Pour déboguer des applications 64 bits localement, Visual Studio utilise un processus de travail 64 bits (msvsmon.exe) pour effectuer les opérations de bas niveau qui ne peuvent pas être réalisées à l’intérieur du processus Visual Studio 32 bits.

 Le débogage en mode mixte n’est pas pris en charge pour les processus 64 bits qui utilisent .NET Framework version 3.5 ou antérieure.

## <a name="debug-a-64-bit-application"></a>Déboguer une application 64 bits
 Pour essayer de déboguer une application 64 bits :

1. Créez une solution Visual Studio, par exemple une application console C#.

2. Définissez une configuration 64 bits à l’aide du Gestionnaire de configurations. Pour plus d'informations, consultez [How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).

3. À ce stade, la version 64 bits du débogueur distant (msvsmon.exe) démarre. Le débogueur s’exécute tant que la solution avec la configuration 64 bits est ouverte.

4. Démarrez le débogage. Vous devez avoir la même expérience qu’avec une configuration 32 bits. Si vous obtenez des erreurs, consultez la section de résolution des problèmes ci-dessous.

## <a name="troubleshooting-64-bit-debugging"></a>Résolution des problèmes de débogage 64 bits
 L’erreur suivante peut s’afficher : « Une opération de débogage 64 bits prend plus de temps que prévu ». Dans ce cas, Visual Studio a envoyé une demande à la version 64 bits de msvsmon.exe et l’obtention du résultat de cette demande a pris beaucoup de temps.

 Deux causes principales peuvent provoquer cette erreur :

- Un logiciel de sécurité réseau installé sur votre ordinateur altère la fiabilité de la pile de mise en réseau, et il a ignoré des paquets qui passent sur localhost. Essayez de désactiver tous les logiciels de sécurité réseau et voyez si le problème est résolu. Si tel est le cas, signalez à votre fournisseur de logiciels de sécurité réseau que le logiciel interfère avec le trafic de localhost.

- Vous rencontrez un problème de blocage ou de performances avec Visual Studio. Si le problème se produit régulièrement, vous pouvez collecter les dumps de Visual Studio (devenv.exe) et le processus de travail (msvsmon.exe), puis les envoyer à Microsoft. Pour plus d’informations sur le signalement d’un problème, consultez [How to Report a Problem with Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Applications 64 bits](https://docs.microsoft.com/dotnet/framework/64-bit-apps)
- [Configuration des programmes pour les processeurs 64 bits](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Prise en charge de l’IDE de Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)
- [Utilisation des fichiers de vidage](../debugger/using-dump-files.md)
- [Remote Debugging](../debugger/remote-debugging.md)