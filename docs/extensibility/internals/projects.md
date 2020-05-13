---
title: Projets Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706212"
---
# <a name="projects"></a>Projets
Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser des fichiers de code source et d’autres ressources qui apparaissent dans **Solution Explorer**. En règle générale, les projets sont des fichiers (par exemple, un fichier .csproj pour un projet C) qui stockent des références à des fichiers de code source et des ressources comme les fichiers bitmap. Les projets vous permettent d’organiser, de construire, de déboiffer et de déployer du code source, des références aux services et bases de données Web et à d’autres ressources. VSPackages peut étendre le système de projet Visual Studio de trois façons principales: *les types de projets*, *les sous-types de projets*, et *les outils personnalisés*.

## <a name="in-this-section"></a>Dans cette section
- [Types de projets](../../extensibility/internals/project-types.md)

 *Les types de projets* ajoutent du soutien pour de nouveaux types de projets, comme les langages de programmation. Par exemple, chaque langue que Visual Studio prend en charge a son propre type de projet, et l’échantillon d’intégration IronPython comprend un type de projet pour la langue IronPython. Vous devez créer un type de projet pour des langues autres que C ou Visual Basic pour personnaliser la façon dont les articles sont construits, débogés, déployés et affichés dans **Solution Explorer**. Pour plus d’informations, voir [Types de projet](../../extensibility/internals/project-types.md).

- [Sous-types de projets](../../extensibility/internals/project-subtypes.md)

 *Les sous-types de projets* sont basés sur les types de projets et peuvent être utilisés pour personnaliser la façon dont les projets sont construits, débogés et déployés. Visual Studio utilise des sous-types de projets avec des projets Smart Device; ils personnalisent le déploiement en copiant un programme nouvellement construit à partir d’un ordinateur de développement à l’appareil cible. Les types de projets C et Visual Basic peuvent servir de base aux sous-types de projets; Les types de projets CMD ne peuvent pas. Vos propres types de projets peuvent également servir de base aux sous-types de projets. Pour plus d’informations, voir [Project Subtypes](../../extensibility/internals/project-subtypes.md).

- [Projets web](../../extensibility/internals/web-projects.md)

 Explique le projet Web, qui à son tour créer des applications Web.

- [Nouvelle génération de projet : Sous le capot, la première et la](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) nouvelle génération de projet : sous le [capot, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Explique ce qui se passe réellement lorsque vous créez un nouveau projet.

- [Échantillons VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contient les échantillons dans le VSSDK qui traitent des projets et des solutions.

## <a name="related-sections"></a>Sections connexes
- [Dans le kit SDK Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Expliquez différents aspects de l’extéabilité visual Studio.
