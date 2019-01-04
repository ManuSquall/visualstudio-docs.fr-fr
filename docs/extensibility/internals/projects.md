---
title: Projets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 893dbdb8a1ff92d338b6e8ee654f60578990c7e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876742"
---
# <a name="projects"></a>Projets
Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser les fichiers de code source et d’autres ressources qui s’affichent dans **l’Explorateur de solutions**. En règle générale, les projets sont des fichiers (par exemple, un fichier .csproj pour un projet c#) qui stockent les références aux fichiers de code source et des ressources telles que des fichiers bitmap. Les projets permettent d’organiser, générer, déboguer et déployer le code source, des références aux services Web et bases de données et d’autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio de trois manières principales : *types de projets*, *les sous-types de projet*, et *outils personnalisés*.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Types de projets](../../extensibility/internals/project-types.md)  
 *Types de projets* ajouter la prise en charge de nouveaux types de projets, tels que les langages de programmation. Par exemple, chaque langage qui prend en charge de Visual Studio a son propre type de projet, et l’exemple d’intégration IronPython inclut un type de projet pour la langue d’IronPython. Vous devez créer un type de projet pour les langages autres que c# ou Visual Basic pour personnaliser comment les éléments sont générés, débogués, déployés et affichées dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Types de projets](../../extensibility/internals/project-types.md).  
  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 *Les sous-types de projet* sont basées sur les types de projets et peut être utilisé pour personnaliser la façon dont les projets sont générés, débogués et déployés. Visual Studio utilise des sous-types de projet avec les projets Smart Device ; ils personnaliser le déploiement en copiant un programme qui vient d’être créé à partir d’un ordinateur de développement à l’appareil cible. Types de projets Visual Basic et c# peuvent servir comme base pour les sous-types de projet ; Vous ne pouvez pas les types de projets C++. Vos propres types de projet peuvent également être utilisés comme base pour les sous-types de projet. Pour plus d’informations, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
 [Projets Web](../../extensibility/internals/web-projects.md)  
 Explique le projet Web, qui à leur tour créent des applications Web.  
  
 [Nouvelle génération de projet : Sous le capot, première partie](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) et [nouvelle génération de projet : Sous le capot, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explique ce qui se produit en fait lorsque vous créez un nouveau projet.  
  
 [Exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples)  
 Contient des exemples de l’extensibilité Visual Studio qui traitent des projets et solutions.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Dans le Kit de développement logiciel (SDK) Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Expliquer les différents aspects de l’extensibilité de Visual Studio.