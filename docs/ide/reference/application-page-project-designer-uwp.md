---
title: Page de propriétés de l’application pour les applications UWP
description: Découvrez comment utiliser la page de l’application pour spécifier l’assembly et les informations du package du projet plateforme Windows universelle (UWP) et cibler la version de Windows 10.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 826d408d8e1a6a2cb8bcad956ce930781a9155db
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871364"
---
# <a name="application-property-page-uwp-projects"></a>Page de propriétés de l’application (projets UWP)

Utilisez la page de propriétés **Application** pour spécifier l’assembly du projet UWP et les informations du package, et la version cible Windows 10.

![Page de propriétés de l'application](media/application-page-uwp.png)

Pour accéder à la page **Application**, choisissez le nœud du projet dans **l’Explorateur de solutions**. Choisissez ensuite **Project**  >  **Propriétés** du projet dans la barre de menus. Les pages de propriétés s’ouvrent sous l’onglet **Application**.

## <a name="general-section"></a>Section Général

Nom de l' **assembly** &mdash; Spécifie le nom du fichier de sortie qui contiendra le manifeste de l’assembly.

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Espace de noms** &mdash; par défaut Spécifie l’espace de noms de base pour les fichiers ajoutés au projet. Pour plus d’informations sur les espaces de noms, consultez [Espaces de noms (Guide de programmation C#)](/dotnet/csharp/programming-guide/namespaces/), [Espaces de noms (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) ou [Espaces de noms (C++)](/cpp/cpp/namespaces-cpp).

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informations sur** &mdash; l’assembly Le choix de ce bouton permet d’afficher la [boîte de dialogue informations de l’assembly](../../ide/reference/assembly-information-dialog-box.md).

**Manifeste** &mdash; du package Le choix de ce bouton ouvre le concepteur de manifeste. Le concepteur de manifeste est également accessible en cliquant sur le fichier _Package.appxmanifest_ dans **l’Explorateur de solutions**. Pour plus d'informations, consultez [Configurer un package avec le concepteur de manifeste](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Section Ciblage

Vous pouvez définir la version cible et la version minimale de Windows 10 pour votre application en utilisant les listes déroulantes dans cette section. Nous vous recommandons de cibler la version la plus récente de Windows 10, et si vous développez une application d’entreprise, de prendre en charge une version minimale antérieure également. Pour plus d’informations sur la version Windows 10 à choisir, consultez [Choisir une version UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Pour plus d’informations sur le ciblage de plateforme dans Visual Studio, consultez [Ciblage de plateforme](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Voir aussi

- [Créer votre première application UWP](/windows/uwp/get-started/your-first-app)
- [Choisir une version UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
