---
title: Éléments essentiels du projet Web | Microsoft Docs
description: Découvrez les détails internes sur le fonctionnement des projets Web dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9442dcdd460e1213c3c07ee87a5ea2e0d7099072
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085700"
---
# <a name="web-project-essentials"></a>Éléments fondamentaux de projet web
Les projets Web créent des applications Web. Vous pouvez utiliser un projet Web pour créer une application Web qui a des pages Web intelligentes. Une page Web intelligente contient du code côté serveur qui restitue la page Web à la demande.

 À l’aide de langages de programmation traditionnels, tels que [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] , vous pouvez créer des pages Web intelligentes pour collecter et traiter les informations d’un utilisateur, les stocker dans une base de données, etc.

- Le modèle code-behind associe les fichiers de code source dépendants aux pages Web avec l’extension de fichier. aspx ou. asmx. Par exemple, Hello. aspx peut avoir le fichier de code source dépendant Hello. aspx. cs.

- Le code côté serveur associé à une page Web intelligente est compilé dans un fichier exécutable qui se trouve dans le dossier/bin du site Web.

- Les fichiers de code source supplémentaires, tels que les classes d’assistance qui ne sont pas associées à une page Web spécifique, se trouvent dans le dossier site Web/App_Code.

  - Un projet de site Web (WSP) génère un fichier exécutable pour chaque page Web intelligente. Des fichiers exécutables supplémentaires sont générés à partir de tous les fichiers de code source dans le dossier/App_Code.

  - Un projet d’application Web (WAP) produit un fichier exécutable unique qui combine le code pour toutes les pages Web intelligentes, ainsi que tous les fichiers sources dans le dossier/App_Code.

- Le fichier solution pour un projet Web se trouve séparément du site Web lui-même. Par défaut, les fichiers solution se trouvent dans \Documents and Settings \\ *YourAccount*\Mes documents \\ *\<Visual Studio ####>* \projets \\ *YourWebSite*.

  > [!NOTE]
  > Si vous souhaitez conserver le fichier de solution avec le site Web, il vous suffit de le déplacer et de le rouvrir.

- Si vous ouvrez un site Web qui n’a pas de fichier solution dans Visual Studio, un nouveau fichier solution est automatiquement généré pour celui-ci.

- Les projets Web n’ont aucun fichier projet. Les informations de projet sont stockées dans le fichier solution, le fichier web.config, et ailleurs.

- L’ajout de propriétés globales à un projet Web crée automatiquement un fichier de stockage dans le dossier de solution du projet Web.

- Une page Web intelligente peut être associée à un langage de programmation côté serveur à l’aide de la directive de page ou de la \<script runat="server"> balise.

- En outre, les pages Web peuvent avoir un nombre quelconque de blocs de script côté client écrits dans n’importe quel langage de script.

- Un système de projet de site Web est implémenté par l’ajout de modèles de projet et d’élément et l’inscription au [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projet.

- Un système WAP est implémenté en tant que sous-type de projet, également appelé une version de projet. Le [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projet est aromatisé par le sous-type WAP pour créer le système WAP. Pour plus d’informations sur les sous-types de projet, consultez sous- [types de projet](../../extensibility/internals/project-subtypes.md).

- Une page Web intelligente combine du HTML avec un langage de programmation côté serveur. La langue côté serveur est appelée langage contenu. Pour prendre en charge un langage contenu, le système de projet Web doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> famille d’interfaces.

  - Pour prendre en charge le langage contenu dans un éditeur, le service de langage HTML doit différer l’affichage du code de langue contenu dans un service de langage contenu.

  - Les marqueurs d’erreur (tildes rouges) doivent toujours être créés dans la mémoire tampon principale de l’éditeur de code.

## <a name="see-also"></a>Voir aussi
- [Projets web](../../extensibility/internals/web-projects.md)
