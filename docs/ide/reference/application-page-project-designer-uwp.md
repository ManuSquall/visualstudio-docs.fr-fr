---
title: "Page de propriétés de l’application pour les applications UWP | Microsoft Docs"
ms.date: 01/23/2018
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- AppPackage.Properties.Application"
helpviewer_keywords:
- Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: 34cb125c33ab36a89601c2492d27841bb2ce49d5
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="application-property-page-uwp-projects"></a>Page de propriétés de l’application (projets UWP)

Utilisez la page de propriétés **Application** pour spécifier l’assembly du projet UWP et les informations du package, et la version cible Windows 10.

![Page de propriétés de l'application](media/application-page-uwp.png)

Pour accéder à la page **Application**, choisissez le nœud du projet dans **l’Explorateur de solutions**. Ensuite, choisissez **Projet** > **Propriétés** dans la barre de menus. Les pages de propriétés s’ouvrent sous l’onglet **Application**.

## <a name="general-section"></a>Section Général

**Nom de l’assembly**&mdash;Spécifie le nom du fichier de sortie qui contient le manifeste de l’assembly.

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Espace de noms par défaut**&mdash;Spécifie l’espace de noms de base pour les fichiers ajoutés au projet. Pour plus d’informations sur les espaces de noms, consultez [Espaces de noms (Guide de programmation C#)](/dotnet/csharp/programming-guide/namespaces/), [Espaces de noms (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) ou [Espaces de noms (C++)](/cpp/cpp/namespaces-cpp).

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informations de l’assembly**&mdash;Cliquez sur ce bouton pour afficher la [boîte de dialogue Informations de l’assembly](../../ide/reference/assembly-information-dialog-box.md).

**Manifeste du package**&mdash;Cliquez sur ce bouton pour ouvrir le concepteur de manifeste. Le concepteur de manifeste est également accessible en cliquant sur le fichier _Package.appxmanifest_ dans **l’Explorateur de solutions**. Pour plus d'informations, consultez [Configurer un package avec le concepteur de manifeste](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Section Ciblage

Vous pouvez définir la version cible et la version minimale de Windows 10 pour votre application en utilisant les listes déroulantes dans cette section. Nous vous recommandons de cibler la version la plus récente de Windows 10, et si vous développez une application d’entreprise, de prendre en charge une version minimale antérieure également. Pour plus d’informations sur la version Windows 10 à choisir, consultez [Choisir une version UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Pour plus d’informations sur le ciblage de plateforme dans Visual Studio 2017, consultez [Ciblage de plateforme](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#a-iddevelopwindows-avisual-studio-2017-support-for-windows-development).

## <a name="see-also"></a>Voir aussi

[Créer votre première application UWP](/windows/uwp/get-started/your-first-app)  
[Choisir une version UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)