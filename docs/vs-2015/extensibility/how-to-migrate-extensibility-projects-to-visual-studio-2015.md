---
title: 'Comment : migrer des projets d’extensibilité vers Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff64d4578a0add2e027af8f6bf93c01e0f32ce24
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282280"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Comment : migrer des projets d’extensibilité vers Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici comment mettre à niveau de votre extension.  
  
> [!IMPORTANT]
>  Si vous souhaitez maintenir une version de votre solution d’extension pour une version antérieure de Visual Studio, veillez à effectuer une copie avant de vous mettre à niveau. Il peut être difficile de revenir de la version mise à niveau à son état précédent.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Pour mettre à niveau une solution d’extensibilité  
  
1.  À l’aide de la copie que vous souhaitez mettre à niveau, ouvrez-le dans la nouvelle version. Vous en êtes averti que la mise à niveau n’est pas réversible.  
  
2.  Une fois la mise à niveau terminée, modifiez le chemin d’accès du programme externe vers la nouvelle version de devenv.exe. Cliquez sur le nœud de projet dans le **l’Explorateur de solutions**, puis choisissez **propriétés**. Dans le **déboguer** onglet, recherchez la zone de texte par **démarrer le programme externe** et modifiez le chemin d’accès de devenv.exe par le chemin d’accès Visual Studio 2015, qui doit ressembler à ceci :  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Ajoutez une référence à Microsoft.VisualStudio.Shell.14.0.dll. (Cliquez sur le nœud de projet dans le **l’Explorateur de solutions** , puis **ajouter / Reference**. Sélectionnez le **Extensions** onglet, puis vérifiez **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Générez la solution. Les fichiers générés sont déployés pour :  
  
     **%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< créer nom\>\\< nom du projet\>\\< Version du projet\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Pour mettre à jour un projet d’extensibilité pour les assemblys de référence NuGet Visual Studio SDK  
  
1.  Déterminer les assemblys de référence de kit de développement logiciel Visual Studio qu'a besoin de votre projet.  Dans **l’Explorateur de solutions**, développez le projet **références** nœud et consultez la liste des références de projet.  Les assemblys de référence de Visual Studio SDK auront le préfixe **Microsoft.VisualStudio** dans le nom (par exemple : Microsoft.VisualStudio.Shell.14.0).  
  
2.  Supprimer les assemblys de référence du Kit de développement logiciel Visual Studio à partir du projet en les sélectionnant, avec le bouton droit sur et **supprimer**.  
  
3.  Ajoutez les versions de NuGet des assemblys de référence du Kit de développement logiciel Visual Studio.  Lorsque vous êtes toujours dans le **références de l’Explorateur de solutions** ouverture d’un nœud, le **gérer les Packages NuGet...** boîte de dialogue.  Si vous souhaitez en savoir plus sur cette boîte de dialogue, consultez [gérer NuGet Packages à l’aide de la boîte de dialogue](http://docs.nuget.org/Consume/Package-Manager-Dialog). Les assemblys de référence du Kit de développement logiciel Visual Studio sont publiées sur [nuget.org](http://www.nuget.org) par [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  À l’aide de **nuget.org** en tant que votre **Source du Package**, recherchez le nom du package NuGet qui correspond à l’assembly de référence souhaitée (par exemple : Microsoft.VisualStudio.Shell.14.0) et installez-le dans votre projet.  NuGet peut ajouter plusieurs assemblys de référence pour satisfaire aux exigences de dépendances de l’assembly initiale.  
  
     Si vous préférez, vous pouvez ajouter à la fois tous les assemblys de référence du Kit de développement logiciel Visual Studio en installant le kit SDK VS [méta package](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Vous pouvez également commencer à utiliser la version de NuGet du Kit de développement logiciel Visual Studio des outils de génération. Ce package NuGet est [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) et une fois ajouté à votre projet inclut les outils nécessaires et cibler les fichiers pour vous permettre de créer votre projet d’extensibilité sur un ordinateur sans le Kit de développement logiciel Visual Studio installé.  
  
> [!NOTE]
>  Il n’est pas nécessaire que vous mettez à jour vos projets d’extensibilité existants pour utiliser les outils et les assemblys de référence NuGet.  Ils peuvent continuer à générer à l’aide des assemblys de référence et les outils installés avec le SDK de Visual Studio.

