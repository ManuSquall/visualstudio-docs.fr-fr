---
title: Projets | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>Projets
Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser les fichiers de code source et d’autres ressources qui s’affichent dans **l’Explorateur de solutions**. En règle générale, les projets sont des fichiers (par exemple, un fichier .csproj pour un projet c#) qui stockent les références aux fichiers de code source et des ressources telles que des fichiers bitmap. Projets permettent d’organiser, générer, déboguer et déployer le code source, des références aux services Web et bases de données et d’autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio dans les trois méthodes principales : *types de projets*, *projet sous-types*, et *des outils personnalisés*.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Types de projets](../../extensibility/internals/project-types.md)  
 *Types de projets* prise en charge de nouveaux types de projets, tels que les langages de programmation. Par exemple, chaque langage prenant en charge de Visual Studio possède son propre type de projet, et l’exemple de l’intégration d’IronPython inclut un type de projet pour le langage IronPython. Vous devez créer un type de projet pour les langages autres que c# ou Visual Basic pour personnaliser comment les éléments sont générés, débogués, déployés et affichés dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Types de projet](../../extensibility/internals/project-types.md).  
  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 *Projet sous-types* sont basées sur les types de projets et peut être utilisé pour personnaliser la façon dont les projets sont générés, débogués et déployés. Visual Studio utilise des sous-types de projets avec les projets Smart Device ; ils personnaliser le déploiement en copiant un programme qui vient d’être créé à partir d’un ordinateur de développement vers le périphérique cible. Types de projets Visual Basic et c# peuvent servir comme base pour les sous-types de projet ; Vous ne pouvez pas les types de projets C++. Vos propres types de projets peuvent également servir comme base pour les sous-types de projet. Pour plus d’informations, consultez [sous-types de projets](../../extensibility/internals/project-subtypes.md).  
  
 [Projets Web](../../extensibility/internals/web-projects.md)  
 Explique le projet Web, qui à son tour créer des applications Web.  
  
 [Nouvelle génération de projet : Dans les coulisses, partie&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) et [nouvelle génération de projet : dans les coulisses, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explique ce qui se produit en fait lorsque vous créez un nouveau projet.  
  
 [Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md)  
 Décrit les exemples de VSSDK qui traitent des projets et solutions.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Dans le Kit de développement logiciel de Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Expliquez les différents aspects de l’extensibilité Visual Studio.
