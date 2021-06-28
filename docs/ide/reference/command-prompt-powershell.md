---
title: Interpréteurs de ligne de commande & demander aux développeurs
description: Démarrez à partir des outils > menu ligne de commande. Visual Studio Invite de commandes développeur, Developer PowerShell et terminal vous permettent d’utiliser plus facilement les outils .NET et C++.
author: TerryGLee
ms.author: tglee
ms.date: 06/11/2021
ms.topic: reference
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: 858845ca5629f64e282e3864daa0201935316062
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990517"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio Invite de commandes développeur et Developer PowerShell

Visual Studio 2019 comprend deux interpréteurs de ligne de commande pour les développeurs :

- **Visual Studio invite de commandes développeur** : une invite de commandes standard avec certaines variables d’environnement définies pour faciliter l’utilisation des outils de développement en ligne de commande. Disponible depuis Visual Studio 2015.

- **Visual Studio Developer PowerShell** -plus puissant qu’une invite de commandes. Par exemple, vous pouvez passer la sortie d’une commande (appelée *cmdlet* ) à une autre cmdlet . Ce Shell a les mêmes variables d’environnement que Invite de commandes développeur. Disponible depuis Visual Studio 2019.


:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Invite de commandes développeur pour Visual Studio avec l’outil CLRVer":::

À compter de Visual Studio 2019 version 16,5, Visual Studio comprend un **Terminal** intégré qui peut héberger l’un de ces shells (invite de commandes développeur et Developer PowerShell). Vous pouvez également ouvrir plusieurs onglets de chaque interpréteur de commandes. Le terminal Visual Studio s’appuie sur le [terminal Windows](/windows/terminal/). Pour ouvrir le terminal dans Visual Studio, choisissez **Afficher** le  >  **Terminal**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Terminal Visual Studio présentant plusieurs onglets":::

Lorsque vous ouvrez l’un des shells de développement à partir de Visual Studio, soit en tant qu’application distincte, soit dans la fenêtre de terminal, il s’ouvre dans le répertoire de votre solution actuelle (si vous avez une solution chargée). Ce comportement permet d’exécuter des commandes sur la solution ou ses projets.

Les deux shells ont des variables d’environnement spécifiques qui vous permettent d’utiliser plus facilement les outils de développement en ligne de commande. Après avoir ouvert l’un de ces shells, vous pouvez entrer les commandes de différents utilitaires sans savoir où ils se trouvent. 

|Commandes populaires|Description|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Générer un projet ou une solution|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| [Outils de .NET Framework](/dotnet/framework/tools/index) pour CLR.|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|[Outil .NET Framework](/dotnet/framework/tools/index) pour le désassembleur.|
|[`dotnet`](/dotnet/core/tools/dotnet)|[Commande CLI .net](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[Commande CLI .net](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Outil de compilation C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Outil de compilation C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Outil de génération C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Outil de génération C/C++|


## <a name="start-in-visual-studio"></a>Démarrer dans Visual Studio

Pour ouvrir Invite de commandes développeur ou Developer PowerShell dans Visual Studio, procédez comme suit :

1. Ouvrez Visual Studio.

1. Dans la barre de menus, choisissez **Outils**  >  **ligne de commande**  >  **invite de commandes développeur** ou **Developer PowerShell**.

   ![Élément de menu d’invite de commandes dans Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Démarrer à partir du menu Windows

Vous pouvez également démarrer les shells à partir du menu Démarrer. Vous pouvez avoir plusieurs invites de commande, en fonction de la version de Visual Studio et de tous les kits de développement logiciel (SDK) et charges de travail supplémentaires que vous avez installés. 

### <a name="windows-10"></a>Windows 10

1. Sélectionnez **Démarrer** ![ la touche de logo Windows sur le clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) et faites défiler jusqu’à la lettre **V**.

1. Développez le dossier **Visual Studio 2019** .

1. Choisissez **invite de commandes développeur pour vs 2019** ou **Developer PowerShell pour vs 2019**.

   Vous pouvez également commencer à taper le nom de l’interpréteur de commandes dans la zone de recherche de la barre des tâches, puis choisir le résultat à partir duquel la liste des résultats commence à afficher les correspondances de recherche.

   ![Image GIF animée montrant le comportement de recherche sur Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows de votre clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) de votre clavier, par exemple.

1. Dans l’écran d' **Accueil** , appuyez sur **CTRL** + **Tab** pour ouvrir la liste des **applications** , puis appuyez sur la touche **V**. Une liste incluant toutes les invites de commandes Visual Studio installées s’affiche.

1. Choisissez **invite de commandes développeur pour vs 2019** ou **Developer PowerShell pour vs 2019**.

### <a name="windows-7"></a>Windows 7

1. Choisissez **Démarrer** , puis développez **tous les programmes**.

1. Choisissez **Visual Studio 2019**  >  **Visual Studio Tools**  >  **invite de commandes développeur pour vs 2019** ou **Developer PowerShell pour vs 2019**.

   ![Menu Démarrer de Windows 7 avec l’invite de commandes en surbrillance](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Si vous avez installé d’autres kits de [développement logiciel (SDK) Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versions antérieures](https://developer.microsoft.com/windows/downloads/sdk-archive), vous pouvez voir des invites de commandes supplémentaires. Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.

## <a name="start-from-file-browser"></a>Démarrer à partir de l’Explorateur de fichiers 

En règle générale, les raccourcis des shells que vous avez installés sont placés dans le dossier **menu Démarrer** de Visual Studio, par exemple dans *%ProgramData%\Microsoft\Windows\Start c:\ProgramData\Microsoft\Windows\Menu Studio 2019 \ Visual Studio Tools*. Toutefois, si la recherche de l’invite de commandes ne produit pas les résultats attendus, vous pouvez essayer de localiser manuellement les fichiers sur votre ordinateur.

### <a name="developer-command-prompt"></a>Invite de commandes développeur

Recherchez le nom du fichier d’invite de commandes, qui est *VsDevCmd.bat*, ou accédez au dossier Tools pour Visual Studio, tel que *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (le chemin change en fonction de la version, de l’édition et de l’emplacement de l’installation de Visual Studio).

Une fois que vous avez localisé le fichier d’invite de commandes, ouvrez-le en entrant la commande suivante dans une fenêtre d’invite de commandes normale :

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Ou entrez la commande suivante dans la boîte de dialogue **exécuter** de Windows :

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Vous devez modifier le chemin d’accès pour qu’il corresponde à votre installation de Visual Studio.

### <a name="developer-powershell"></a>PowerShell Developer

Recherchez un fichier de script PowerShell nommé *Launch-VsDevShell.ps1* ou accédez au dossier Tools pour Visual Studio, tel que *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools*. (Le chemin d’accès change en fonction de la version, de l’édition et de l’emplacement d’installation de Visual Studio.) Une fois que vous avez localisé le fichier PowerShell, exécutez-le en entrant la commande suivante à une invite Windows PowerShell ou PowerShell 6 :

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Par défaut, le développeur PowerShell qui lance est configuré pour l’installation de Visual Studio dont se trouve le chemin d’installation du fichier *Launch-VsDevShell.ps1* .

> [!TIP]
> La [stratégie d’exécution](/powershell/module/microsoft.powershell.core/about/about_execution_policies) doit être définie pour que l' cmdlet s’exécute.

## <a name="see-also"></a>Voir aussi

- [PowerShell Developer](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Disons Hello vers le nouveau terminal Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Terminal Windows](/windows/terminal/)
- [Outils du .NET Framework](/dotnet/framework/tools/index)
- [Gérer les outils externes](../managing-external-tools.md)
- [Utiliser l’ensemble d’outils Microsoft C++ à partir de la ligne de commande](/cpp/build/building-on-the-command-line)
