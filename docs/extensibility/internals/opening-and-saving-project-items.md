---
title: Ouvrir et enregistrer des éléments de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77a3417bc15bc9c4c6149b4e77dc4fdcebe5cd6e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314934"
---
# <a name="opening-and-saving-project-items"></a>Ouverture et enregistrement d’éléments de projet
Lorsque vous ajoutez un nouveau type de projet, vous devez gérer l’ouverture et l’enregistrement de vos fichiers de projets dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Les rubriques suivantes décrivent les différentes approches pour ouvrir et enregistrer des fichiers.

## <a name="in-this-section"></a>Dans cette section
- [Affichage de fichiers à l’aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Fournit une explication pas à pas de la façon dont l’IDE gère le **ouvrir un fichier** commande et le rôle de projets dans la réponse à cette commande.

- [Affichage de fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fournit une explication détaillée, étape par étape de la façon dont l’IDE gère le **ouvrir avec** commande, demande l’ouverture d’un fichier qui a le choix des éditeurs standards.

- [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)

 Fournit des instructions détaillées permettant de spécifier que les fichiers d’un type particulier dans votre projet doivent être ouvert à l’aide d’un éditeur spécifique au projet.

- [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)

 Fournit des instructions détaillées pour la spécification de l’activation de l’IDE ouvrir un éditeur standard pour les fichiers dans votre type de projet.

- [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)

 Fournit des instructions détaillées pour ouvrir un éditeur spécifique au projet pour un fichier ouvert.

- [Enregistrement d’un document standard](../../extensibility/internals/saving-a-standard-document.md)

 Fournit une explication détaillée de la façon dont l’IDE gère le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes pour un document ouvert dans un éditeur standard.

- [Enregistrement d’un document personnalisé](../../extensibility/internals/saving-a-custom-document.md)

 Fournit un diagramme et une explication détaillée de la façon dont l’IDE gère le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes pour les documents ouverts dans un éditeur personnalisé.

- [Déterminer quel éditeur ouvre un fichier dans un projet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Décrit le processus qui l’IDE suit pour sélectionner l’éditeur approprié ou le concepteur pour un fichier.

## <a name="related-sections"></a>Rubriques connexes
- [Création d’éditeurs et de concepteurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md)

 Répertorie les quatre types d’éditeurs que l’IDE peut héberger et donne les descriptions de chaque éditeur.

- [Types de projets](../../extensibility/internals/project-types.md)

 Explique comment les projets contrôlent la façon dont le code est compilé et généré, mode d’ouverture des éditeurs, et comment les éléments de projet sont mis en forme.