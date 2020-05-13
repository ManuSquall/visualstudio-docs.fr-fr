---
title: Éléments du projet d’ouverture et d’épargne (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706967"
---
# <a name="opening-and-saving-project-items"></a>Ouverture et enregistrement d’éléments de projet
Lorsque vous ajoutez un nouveau type de projet, vous devez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gérer l’ouverture et l’enregistrement de vos fichiers de projets dans l’environnement de développement intégré (IDE). Les sujets suivants discutent des différentes approches d’ouverture et d’enregistrement des fichiers.

## <a name="in-this-section"></a>Dans cette section
- [Affichage de fichiers à l’aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Fournit une explication étape par étape de la façon dont l’IDE gère la commande **Open File** et le rôle des projets dans la réponse à cette commande.

- [Affichage de fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fournit une explication détaillée, étape par étape de la façon dont l’IDE gère **l’Open With** commande, incitant l’ouverture d’un fichier qui a un certain choix d’éditeurs standard.

- [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)

 Fournit des instructions étape par étape pour spécifier que les fichiers d’un type particulier dans votre projet doivent être ouverts à l’aide d’un éditeur spécifique au projet.

- [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)

 Fournit des instructions étape par étape pour spécifier comment permettre à l’IDE d’ouvrir un éditeur standard pour les fichiers dans votre type de projet.

- [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)

 Fournit des instructions étape par étape pour ouvrir un éditeur spécifique au projet pour un fichier ouvert.

- [Enregistrement d’un document standard](../../extensibility/internals/saving-a-standard-document.md)

 Fournit une explication détaillée de la façon dont l’IDE gère **l’enregistrer**, **enregistrer comme**, et enregistrer **toutes les** commandes pour un document ouvert dans un éditeur standard.

- [Enregistrement d’un document personnalisé](../../extensibility/internals/saving-a-custom-document.md)

 Fournit un diagramme et une explication détaillée de la façon dont l’IDE gère **l’enregistrer**, **enregistrer comme**, et enregistrer toutes les commandes pour **les** documents ouverts dans un éditeur personnalisé.

- [Déterminer quel éditeur ouvre un fichier dans un projet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Discute du processus suivi par l’IDE pour sélectionner l’éditeur ou le concepteur approprié pour un fichier.

## <a name="related-sections"></a>Sections connexes
- [Création d’éditeurs et de concepteurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md)

 Répertorie les quatre types d’éditeurs que l’IDE peut héberger et donne des descriptions de chaque éditeur.

- [Types de projets](../../extensibility/internals/project-types.md)

 Discute de la façon dont les projets contrôlent la façon dont le code est compilé et construit, comment les éditeurs sont ouverts et comment les éléments du projet sont formatés.
