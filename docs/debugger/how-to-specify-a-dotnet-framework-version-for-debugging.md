---
title: Spécifier une version de .NET Framework pour le débogage | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bfe17100fcdcb0d475a7467233caa51ba7895225
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747474"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Procédure : Spécifier une Version du .NET Framework pour le débogage (C#, Visual Basic, F#)

Le débogueur Visual Studio prend en charge le débogage des versions antérieures de Microsoft .NET Framework, ainsi que la version actuelle. Si vous démarrez une application à partir de Visual Studio, le débogueur identifie toujours la version correcte du .NET Framework pour l’application que vous déboguez. Toutefois, si l’application est déjà en cours d’exécution et que vous démarrez le débogage à l’aide de **attacher à**, le débogueur pas peut toujours être en mesure d’identifier une version antérieure du .NET Framework. Si cela se produit, un message d'erreur s'affiche qui indique,

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

Dans de rares cas où cette erreur apparaît, vous pouvez définir une clé de Registre pour indiquer au débogueur la version à utiliser.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Pour spécifier une version .NET Framework pour le débogage

1. Recherchez dans le répertoire Windows\Microsoft.NET\Framework les versions du .NET Framework installées sur votre ordinateur. Les numéros de version sont similaires à ceci :

    `V1.1.4322`

    Identifiez le numéro de version correct et prenez-en note.

2. Démarrez l’**Éditeur du Registre** (regedit).

3. Dans l’**Éditeur du Registre**, ouvrez le dossier HKEY_LOCAL_MACHINE.

4. Accédez à : HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Si la clé n’existe pas, cliquez avec le bouton droit sur HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, puis cliquez sur **Nouvelle clé**. Nommez la nouvelle clé `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. Après avoir accédé à {449EC4CC-30D2-4032-9256-EE18EB41B62B}, recherchez la clé CLRVersionForDebugging dans la colonne **Nom**.

   1. Si la clé n’existe pas, cliquez avec le bouton droit sur {449EC4CC-30D2-4032-9256-EE18EB41B62B}, puis cliquez sur **Nouvelle valeur de chaîne**. Puis cliquez sur la nouvelle valeur de chaîne, cliquez sur **renommer**et le type `CLRVersionForDebugging`.

6. Double-cliquez sur **CLRVersionForDebugging**.

7. Dans la zone **Modification de la chaîne**, tapez le numéro de version du .NET Framework dans la zone **Valeur**. Exemple : V1.1.4322

8. Cliquez sur **OK**.

9. Fermez l’**Éditeur du Registre**.

     Si vous obtenez encore un message d'erreur lorsque vous commencez à déboguer, vérifiez que vous avez entré correctement le numéro de version dans le Registre. Vérifiez également que vous utilisez une version du .NET Framework prises en charge par Visual Studio. Le débogueur est compatible avec la version actuelle et les versions antérieures du .NET Framework, mais il n'offre peut-être pas une compatibilité ascendante avec les futures versions.

## <a name="see-also"></a>Voir aussi
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)