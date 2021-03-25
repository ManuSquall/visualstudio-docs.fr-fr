---
title: Ouverture et enregistrement d’éléments de projet | Microsoft Docs
description: Découvrez les différentes approches de l’ouverture et de l’enregistrement de fichiers pour votre nouveau type de projet dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ff3c76294ce99fa5eeb7bf311307e54f5d0e6cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063069"
---
# <a name="opening-and-saving-project-items"></a>Ouverture et enregistrement d’éléments de projet
Lorsque vous ajoutez un nouveau type de projet, vous devez gérer l’ouverture et l’enregistrement de vos fichiers de projet dans l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE). Les rubriques suivantes décrivent les différentes approches de l’ouverture et de l’enregistrement des fichiers.

## <a name="in-this-section"></a>Dans cette section
- [Affichage de fichiers à l’aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Fournit une explication pas à pas de la façon dont l’IDE gère la commande **ouvrir un fichier** et le rôle des projets qui répondent à cette commande.

- [Affichage de fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fournit une explication pas à pas détaillée de la façon dont l’IDE gère la commande **Ouvrir avec** , en invitant l’ouverture d’un fichier qui a un certain nombre d’éditeurs standard.

- [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)

 Fournit des instructions pas à pas pour spécifier que les fichiers d’un type particulier dans votre projet doivent être ouverts à l’aide d’un éditeur spécifique au projet.

- [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)

 Fournit des instructions pas à pas pour spécifier comment permettre à l’IDE d’ouvrir un éditeur standard pour les fichiers dans votre type de projet.

- [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)

 Fournit des instructions pas à pas pour ouvrir un éditeur spécifique à un projet pour un fichier ouvert.

- [Enregistrement d’un document standard](../../extensibility/internals/saving-a-standard-document.md)

 Fournit une explication détaillée de la façon dont l’IDE gère les commandes **Enregistrer**, **Enregistrer sous** et **enregistrer toutes les** commandes d’un document ouvert dans un éditeur standard.

- [Enregistrement d’un document personnalisé](../../extensibility/internals/saving-a-custom-document.md)

 Fournit un diagramme et une explication détaillée de la façon dont l’IDE gère les commandes **Enregistrer**, **Enregistrer sous** et **enregistrer toutes les** documents ouverts dans un éditeur personnalisé.

- [Déterminer quel éditeur ouvre un fichier dans un projet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Décrit le processus que l’IDE suit pour sélectionner l’éditeur ou le concepteur approprié pour un fichier.

## <a name="related-sections"></a>Sections connexes
- [Création d’éditeurs et de concepteurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md)

 Répertorie les quatre types d’éditeurs que l’IDE peut héberger et fournit les descriptions de chaque éditeur.

- [Types de projets](../../extensibility/internals/project-types.md)

 Explique comment les projets contrôlent la façon dont le code est compilé et généré, comment les éditeurs sont ouverts et comment les éléments de projet sont mis en forme.
