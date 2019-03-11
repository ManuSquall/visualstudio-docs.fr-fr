---
title: Page de propriétés de l’application pour les applications UWP
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 416661a39f54429f24cca66a0ec1be7b6c87629d
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222712"
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

Pour plus d’informations sur le ciblage de plateforme dans Visual Studio, consultez [Ciblage de plateforme](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Voir aussi

- [Créer votre première application UWP](/windows/uwp/get-started/your-first-app)
- [Choisir une version UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)