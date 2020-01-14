---
title: 'Comment : migrer des projets d’extensibilité vers Visual Studio 2015 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2f4926a503304491164635b983353ba7f3bb0f6
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915982"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Comment : migrer des projets d’extensibilité vers Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici comment mettre à niveau votre extension.  
  
> [!IMPORTANT]
> Si vous envisagez de conserver une version de votre solution d’extension pour une version antérieure de Visual Studio, veillez à effectuer une copie avant d’effectuer la mise à niveau. Il peut être difficile de ramener la version mise à niveau à son état précédent.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Pour mettre à niveau une solution d’extensibilité  
  
1. À l’aide de la copie que vous souhaitez mettre à niveau, ouvrez-la dans la nouvelle version. Vous serez informé que la mise à niveau n’est pas réversible.  
  
2. Une fois la mise à niveau terminée, remplacez le chemin d’accès du programme externe par la nouvelle version de devenv. exe. Cliquez avec le bouton droit sur le nœud du projet dans le **Explorateur de solutions**, puis choisissez **Propriétés**. Dans l’onglet **Déboguer** , recherchez la zone de texte par **Démarrer le programme externe** et remplacez le chemin de devenv. exe par le chemin d’accès Visual Studio 2015, qui doit ressembler à ceci :  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE\devenv.exe**  
  
3. Ajoutez une référence à Microsoft. VisualStudio. Shell. 14.0. dll. (Cliquez avec le bouton droit sur le nœud du projet dans le **Explorateur de solutions** puis sélectionnez **Ajouter/référencer**. Sélectionnez l’onglet **Extensions** , puis vérifiez **Microsoft. VisualStudio. Shell. 14.0**.)  
  
4. Générez la solution. Les fichiers générés sont déployés dans :  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nom de l’auteur\>\\< nom du projet** \>\\\>\\.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Pour mettre à jour un projet d’extensibilité dans des assemblys de référence NuGet VS SDK  
  
1. Déterminez les assemblys de référence du kit de développement Visual Studio dont votre projet a besoin.  Dans **Explorateur de solutions**, développez le nœud **références** du projet et passez en revue la liste des références de projet.  Les références aux assemblys du SDK VS auront le préfixe **Microsoft. VisualStudio** dans le nom (par exemple : Microsoft. VisualStudio. Shell. 14.0).  
  
2. Supprimez les assemblys de référence du kit de développement Visual Studio du projet en les sélectionnant, cliquez avec le bouton droit et **supprimez**.  
  
3. Ajoutez les versions NuGet des assemblys de référence du kit de développement logiciel (SDK) VS.  Toujours dans le nœud **Explorateur de solutions références** , ouvrez gérer les **packages NuGet...** dialogue.  Si vous souhaitez en savoir plus sur cette boîte de dialogue, consultez [gérer les packages NuGet à l’aide de la boîte de dialogue](/nuget/consume-packages/install-use-packages-visual-studio). Les assemblys de référence du kit de développement logiciel VS SDK sont publiés sur [NuGet.org](https://www.nuget.org/) par [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. À l’aide de **NuGet.org** comme **source de package**, recherchez le nom du package NuGet qui correspond à l’assembly de référence souhaité (par exemple : Microsoft. VisualStudio. Shell. 14.0) et installez-le dans votre projet.  NuGet peut ajouter plusieurs assemblys de référence afin de satisfaire les dépendances de l’assembly initial.  
  
     Si vous préférez, vous pouvez ajouter tous les assemblys de référence du kit de développement logiciel (SDK) Visual Studio à la fois en installant le [package Meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK vs.  
  
5. Vous pouvez également passer à l’utilisation de la version NuGet des outils de génération du kit de développement logiciel (SDK) Visual Studio. Ce package NuGet est [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) et, une fois ajouté à votre projet, inclut les outils et les fichiers cibles nécessaires pour vous permettre de générer votre projet d’extensibilité sur un ordinateur sur lequel le kit de développement logiciel (SDK) Visual Studio n’est pas installé.  
  
> [!NOTE]
> Il n’est pas nécessaire de mettre à jour vos projets d’extensibilité existants pour utiliser les outils et assemblys de référence NuGet.  Ils peuvent continuer à créer à l’aide des assemblys de référence et des outils installés avec le kit de développement logiciel (SDK) Visual Studio.
