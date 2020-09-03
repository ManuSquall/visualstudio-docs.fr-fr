---
title: Projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a251af12ccf4be5f0f48f789ac59fedaed3299b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183945"
---
# <a name="projects"></a>Projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser les fichiers de code source et d’autres ressources qui s’affichent dans **Explorateur de solutions**. En règle générale, les projets sont des fichiers (par exemple, un fichier. csproj pour un projet C#) qui stockent des références à des fichiers de code source et à des ressources telles que des fichiers bitmap. Les projets vous permettent d’organiser, de générer, de déboguer et de déployer du code source, des références à des services Web et à des bases de données, ainsi que d’autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio de trois manières principales : *types de projets*, sous- *types de projet*et *outils personnalisés*.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Les *types* de projets ajoutent la prise en charge de nouveaux genres de projets, tels que des langages de programmation. Par exemple, chaque langage que Visual Studio prend en charge possède son propre type de projet, et l’exemple d’intégration IronPython inclut un type de projet pour le langage IronPython. Vous devez créer un type de projet pour les langages autres que C# ou Visual Basic pour personnaliser la façon dont les éléments sont générés, débogués, déployés et affichés dans **Explorateur de solutions**. Pour plus d’informations, consultez [types de projets](../../extensibility/internals/project-types.md).  
  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 Les sous- *types de projet* sont basés sur des types de projet et peuvent être utilisés pour personnaliser la façon dont les projets sont générés, débogués et déployés. Visual Studio utilise des sous-types de projet avec des projets Smart Device. ils personnalisent le déploiement en copiant un programme nouvellement généré à partir d’un ordinateur de développement vers l’appareil cible. Les types de projets C# et Visual Basic peuvent être utilisés comme base pour les sous-types de projet ; Les types de projets C++ ne peuvent pas. Vos propres types de projets peuvent également servir de base pour les sous-types de projet. Pour plus d’informations, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
 [Projets web](../../extensibility/internals/web-projects.md)  
 Décrit le projet Web, qui à son tour, crée des applications Web.  
  
 [Nouvelle génération de projet : en coulisses, première](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) et [nouvelle génération de projet : en coulisses, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explique ce qui se produit réellement lorsque vous créez un projet.  
  
 [Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md)  
 Décrit les exemples du VSSDK qui traitent des projets et des solutions.  
  
## <a name="related-sections"></a>Sections connexes  
 [Dans le kit SDK Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Expliquer les différents aspects de l’extensibilité de Visual Studio.
