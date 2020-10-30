---
title: Dépannage des erreurs de ciblage du .NET Framework | Microsoft Docs
description: Découvrez les erreurs MSBuild qui peuvent se produire en raison de problèmes de référence et comment vous pouvez résoudre ces erreurs.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98c3ba64454ca25b62dc5dbe0964db64b010a7ec
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046984"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Résoudre les erreurs de ciblage de .NET Framework

Cette rubrique décrit les erreurs MSBuild qui peuvent se produire en raison de problèmes de référence et la façon dont vous pouvez résoudre ces erreurs.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Vous avez fait référence à un projet ou à un assembly qui cible une autre version de .NET Framework

 Vous pouvez créer des applications qui référencent des projets ou des assemblys ciblant différentes versions du .NET Framework. Par exemple, vous pouvez créer une application qui cible le profil client pour le .NET Framework 4, mais qui référence un assembly ciblant le .NET Framework 2.0. Cependant, si vous créez un projet qui cible une version antérieure du .NET Framework, vous ne pouvez pas définir une référence dans ce projet à un projet ou à un assembly qui cible le profil client pour le .NET Framework 4 ou le .NET Framework 4 lui-même. Pour résoudre cette erreur, vérifiez que votre application cible un ou plusieurs profils qui sont compatibles avec le profil ciblé par les projets ou assemblys référencés par votre application.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Vous avez reciblé un projet vers une autre version de .NET Framework

 Si vous changez la version cible du .NET Framework pour votre application, Visual Studio change certaines des références, mais vous devrez peut-être en modifier d’autres manuellement. Par exemple, l’une des erreurs mentionnées précédemment peut se produire si vous modifiez une application pour cibler le .NET Framework 3,5 Service Pack 1 et que cette application possède des ressources ou des paramètres qui reposent sur le profil client pour le .NET Framework 4.

 Pour contourner les paramètres d’application, ouvrez **l’Explorateur de solutions** , choisissez **Afficher tous les fichiers** , puis modifiez le fichier *app.config* dans l’éditeur XML de Visual Studio. Modifiez la version dans les paramètres pour la faire correspondre à celle du .NET Framework. Par exemple, vous pouvez remplacer le paramètre de version 4.0.0.0 par 2.0.0.0. De même, pour une application comportant des ressources supplémentaires, ouvrez **l’Explorateur de solutions** , choisissez le bouton **Afficher tous les fichiers** , développez **Mon projet** (Visual Basic) ou **Propriétés** (C#), puis modifiez le fichier *Resources.resx* dans l’éditeur XML de Visual Studio. Remplacez le paramètre de version 4.0.0.0 par 2.0.0.0.

 Si votre application dispose de ressources telles que des icônes, des images ou des paramètres tels que des chaînes de connexion de données, vous pouvez également résoudre l’erreur en supprimant tous les éléments de la page **Paramètres** du **Concepteur de projets** et en rajoutant ensuite les paramètres exigés.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Vous avez reciblé un projet vers une autre version de .NET Framework et les références ne sont pas résolues

 Si vous reciblez un projet vers une autre version du .NET Framework, il peut arriver que vos références ne soient pas correctement résolues. Ce problème est souvent causé par des références explicites complètes aux assemblys. Vous pouvez y remédier en supprimant les références non résolues et en les rajoutant ensuite au projet. Vous pouvez également modifier le fichier projet pour remplacer les références. Premièrement, vous supprimez les références de la forme suivante :

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Ensuite, vous les remplacez par la forme simplifiée :

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Après la fermeture et la ré-ouverture votre projet, vous devez également le régénérer pour vérifier que toutes les références sont correctement résolues.

## <a name="see-also"></a>Voir aussi

- [Guide pratique : Cibler une version de .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Profil client .NET Framework](/dotnet/framework/deployment/client-profile)
- [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md)
- [MULTICIBLAGE](../msbuild/msbuild-multitargeting-overview.md)
