---
title: Projet Web Essentiels (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703548"
---
# <a name="web-project-essentials"></a>Éléments fondamentaux de projet web
Les projets Web créent des applications Web. Vous pouvez utiliser un projet Web pour créer une application Web qui a des pages Web intelligentes. Une page Web intelligente dispose d’un code côté serveur qui rend la page Web à la demande.

 En utilisant des langages de programmation traditionnels, tels que [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]vous pouvez créer des pages Web intelligentes pour recueillir et traiter les informations d’un utilisateur, les stocker dans une base de données, et ainsi de suite.

- Le modèle de code-derrière associe les fichiers de code source dépendants avec des pages Web qui ont l’extension de fichier .aspx ou .asmx. Par exemple, hello.aspx peut avoir le fichier de code source à charge hello.aspx.cs.

- Le code côté serveur associé à une page Web intelligente est compilé dans un fichier exécutable qui est situé dans le site Web /bin dossier.

- D’autres fichiers de code source, tels que les classes d’aide qui ne sont pas associés à une page Web spécifique, sont situés dans le site Web /App_Code dossier.

  - Un projet de site Web (WSP) génère un fichier exécutable pour chaque page Web intelligente. D’autres fichiers exécutables sont générés à partir de tous les fichiers de code source dans le dossier /App_Code.

  - Un projet d’application Web (WAP) produit un seul fichier exécutable qui combine le code pour toutes les pages Web intelligentes, ainsi que tous les fichiers source dans le dossier /App_Code.

- Le fichier de solution pour un projet Web est situé séparément du site Web lui-même. Par défaut, les fichiers de solutions\\sont situés à l’adresse «Documents et Paramètres\\de votre compte à*l’adresse*»Mes documents\\*\<Visual Studio >*'Projets*YourWebSite*.

  > [!NOTE]
  > Si vous voulez conserver le fichier de solution avec le site Web, il suffit de le déplacer là et le rouvrir.

- Si vous ouvrez un site Web qui n’a pas de fichier de solution dans Visual Studio, un nouveau fichier de solution est automatiquement généré pour lui.

- Les projets Web n’ont pas de fichiers de projet. Les informations du projet sont stockées dans le fichier de solution, le fichier web.config et ailleurs.

- L’ajout de propriétés globales à un projet Web crée automatiquement un fichier de stockage dans le dossier de solutions de projet Web.

- Une page Web intelligente peut être associée à un langage de \<programmation côté serveur en utilisant la directive Page ou le script runat"server"> tag.

- En outre, les pages Web peuvent avoir n’importe quel nombre de blocs de script côté client écrits dans n’importe quel langage de script.

- Un système de projet de site Web est mis [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] en œuvre en ajoutant des modèles de projets et d’éléments et en s’inscrivant au projet.

- Un système WAP est mis en œuvre comme un sous-type de projet, également appelé une saveur de projet. Le [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projet est aromatisé par le sous-type WAP pour créer le système WAP. Pour plus d’informations sur les sous-types de projets, voir [Les sous-types du projet](../../extensibility/internals/project-subtypes.md).

- Une page Web intelligente combine HTML avec un langage de programmation côté serveur. La langue côté serveur est appelée la langue contenue. Pour soutenir une langue contenue, le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> système de projet Web doit mettre en œuvre la famille des interfaces.

  - Pour soutenir la langue contenue dans un éditeur, le service de langue HTML doit reporter l’affichage du code de langage contenu à un service linguistique contenu.

  - Les marqueurs d’erreur (squigglies rouges) doivent toujours être créés dans le tampon principal de l’éditeur de code.

## <a name="see-also"></a>Voir aussi
- [Projets web](../../extensibility/internals/web-projects.md)
