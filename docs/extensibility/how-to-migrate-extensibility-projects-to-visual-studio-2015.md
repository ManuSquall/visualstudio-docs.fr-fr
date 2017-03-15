---
title: "Comment&#160;: migrer les projets d’extensibilit&#233; Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de Visual Studio, la mise à niveau"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: migrer les projets d’extensibilit&#233; Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Voici comment mettre à niveau votre extension.  
  
> [!IMPORTANT]
>  Si vous souhaitez maintenir une version de votre solution d’extension pour une version antérieure de Visual Studio, veillez à faire une copie avant de vous mettre à niveau. Il peut être difficile de revenir de la version mise à niveau à son état précédent.  
  
#### Pour mettre à niveau une solution d’extensibilité  
  
1.  À l’aide de la copie que vous souhaitez mettre à niveau, l’ouvrir dans la nouvelle version. Vous serez informées que la mise à niveau n’est pas réversible.  
  
2.  Une fois la mise à niveau terminée, modifiez le chemin d’accès du programme externe vers la nouvelle version de devenv.exe. Cliquez sur le nœud de projet dans le **l’Explorateur de solutions**, puis choisissez **propriétés**. Dans le **Debug** onglet, recherchez la zone de texte par **Démarrer le programme externe** et modifiez le chemin d’accès de devenv.exe pour le chemin d’accès de Visual Studio 2015, qui doit ressembler à ceci :  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  Ajoutez une référence à Microsoft.VisualStudio.Shell.14.0.dll. \(Cliquez sur le nœud de projet dans le **l’Explorateur de solutions** puis **Ajouter \/ Reference**. Sélectionnez le **Extensions** onglet, puis vérifiez **Microsoft.VisualStudio.Shell.14.0**.\)  
  
4.  Générez la solution. Les fichiers créés sont déployées dans :  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< nom de l’auteur \> \\ \< nom du projet \> \\ \< Version du projet \> \\**.  
  
#### Pour mettre à jour un projet d’extensibilité pour les assemblys de référence du SDK de Visual Studio NuGet  
  
1.  Déterminer les assemblys de référence du Kit de développement logiciel Visual Studio qu'a besoin de votre projet.  Dans **l’Explorateur de solutions**, développez le projet **références** nœud et examinez la liste des références de projet.  Kit de développement logiciel Visual Studio référence les assemblys auront le préfixe **Microsoft.VisualStudio** dans le nom \(par exemple : Microsoft.VisualStudio.Shell.14.0\).  
  
2.  Supprimer des assemblys de référence du Kit de développement logiciel Visual Studio à partir du projet en les sélectionnant, cliquez avec le bouton droit et **Supprimer**.  
  
3.  Ajoutez les versions NuGet des assemblys de référence du Kit de développement logiciel Visual Studio.  Toujours dans le **références de l’Explorateur de solutions** ouverture d’un nœud, le **Gérer les Packages NuGet...** boîte de dialogue.  Si vous souhaitez en savoir plus sur cette boîte de dialogue, consultez la page [Gérer NuGet Packages à l’aide de la boîte de dialogue](http://docs.nuget.org/Consume/Package-Manager-Dialog). Les assemblys de référence du Kit de développement logiciel Visual Studio sont publiées sur [nuget.org](http://www.nuget.org) par [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  À l’aide de **nuget.org** comme votre **Source du Package**, recherchez le nom du package NuGet qui correspond à l’assembly de référence de votre choix \(par exemple : Microsoft.VisualStudio.Shell.14.0\) et installez\-le dans votre projet.  NuGet peut ajouter plusieurs assemblys de référence afin de satisfaire les dépendances de l’assembly d’origine.  
  
     Si vous préférez, vous pouvez ajouter simultanément tous les assemblys de référence du Kit de développement logiciel Visual Studio en installant le Kit de développement logiciel Visual Studio [package de métadonnées](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Vous pouvez également basculer vers à l’aide de la version des outils de génération Visual Studio SDK NuGet. Ce package NuGet est [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) et une fois ajouté à votre projet inclut les outils nécessaires et cibler les fichiers pour vous permettre de générer votre projet d’extensibilité sur un ordinateur sans le Kit de développement Visual Studio installé.  
  
> [!NOTE]
>  Il n’est pas nécessaire que vous mettez à jour vos projets d’extensibilité existants pour utiliser les outils et les assemblys de référence NuGet.  Ils peuvent continuer à créer à l’aide des assemblys de référence et des outils installés avec le Kit de développement Visual Studio.