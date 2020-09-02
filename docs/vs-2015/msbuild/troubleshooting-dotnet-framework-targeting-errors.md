---
title: Dépannage des erreurs de ciblage du .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703789"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Dépannage des erreurs de ciblage du .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les erreurs MSBuild qui peuvent se produire en raison de problèmes de référence et la façon dont vous pouvez résoudre ces erreurs.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Vous avez référencé un projet ou un assembly qui cible une version différente du .NET Framework  
 Vous pouvez créer des applications qui référencent des projets ou des assemblys ciblant différentes versions du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Par exemple, vous pouvez créer une application qui cible le profil client pour le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], mais référence un assembly qui cible le .NET Framework 2.0. Toutefois, si vous créez un projet qui cible une version antérieure du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], vous ne pouvez pas définir une référence dans ce projet à un projet ou un assembly qui cible le profil client pour le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lui-même. Pour résoudre cette erreur, vérifiez que votre application cible un ou plusieurs profils qui sont compatibles avec le profil ciblé par les projets ou assemblys référencés par votre application.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Vous avez reciblé un projet vers une autre version du .NET Framework  
 Si vous modifiez la version cible du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pour votre application, Visual Studio met à jour certaines références, mais vous devrez peut-être en modifier d’autres manuellement. Par exemple, si vous modifiez une application pour qu’elle cible le [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] et que cette application dispose de ressources ou de paramètres qui s’appuient sur le profil client du [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], l’une des erreurs mentionnées précédemment peut-se produire.  
  
 Pour contourner les paramètres d’application, ouvrez **l’Explorateur de solutions**, choisissez **Afficher tous les fichiers**, puis modifiez le fichier app.config dans l’éditeur XML de Visual Studio. Modifiez la version dans les paramètres pour la faire correspondre à celle du .NET Framework. Par exemple, vous pouvez remplacer le paramètre de version 4.0.0.0 par 2.0.0.0. De même, pour une application comportant des ressources supplémentaires, ouvrez **l’Explorateur de solutions**, choisissez le bouton **Afficher tous les fichiers**, développez **Mon projet** (Visual Basic) ou **Propriétés** (C#), puis modifiez le fichier Resources.resx dans l’éditeur XML de Visual Studio. Remplacez le paramètre de version 4.0.0.0 par 2.0.0.0.  
  
 Si votre application dispose de ressources telles que des icônes, des images ou des paramètres tels que des chaînes de connexion de données, vous pouvez également résoudre l’erreur en supprimant tous les éléments de la page **Paramètres** du **Concepteur de projets** et en rajoutant ensuite les paramètres exigés.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Vous avez reciblé un projet vers une autre version de .NET Framework et les références ne sont pas résolues  
 Si vous reciblez le projet vers une autre version du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], il peut arriver que vos références ne soient pas correctement résolues. Ce problème est souvent causé par des références explicites complètes aux assemblys. Vous pouvez y remédier en supprimant les références non résolues et en les rajoutant ensuite au projet. Vous pouvez également modifier le fichier projet pour remplacer les références. Premièrement, vous supprimez les références de la forme suivante :  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Ensuite, vous les remplacez par la forme simplifiée :  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> Après la fermeture et la ré-ouverture votre projet, vous devez également le régénérer pour vérifier que toutes les références sont correctement résolues.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Profil client .NET Framework](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Ciblage d’une version de .NET Framework spécifique](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [MULTICIBLAGE](../msbuild/msbuild-multitargeting-overview.md)
