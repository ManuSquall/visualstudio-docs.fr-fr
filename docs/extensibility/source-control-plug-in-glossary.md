---
title: Glossaire du plug-in de contrôle de code source | Microsoft Docs
description: Cet article comprend des termes et définitions utiles relatifs à la documentation du kit de développement logiciel (SDK) du plug-in de contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05b215de4191362a539d3b03ac858da6bb7ee292
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899522"
---
# <a name="source-control-plug-in-glossary"></a>Glossaire de plug-in de contrôle de code source
Les termes et définitions utiles suivants concernent la documentation du kit de développement logiciel (SDK) du plug-in de contrôle de code source.

## <a name="definitions"></a>Définitions
 Archiver lorsqu’un utilisateur apporte des modifications à une copie de travail, un utilisateur doit envoyer des modifications à partir de la copie de travail dans le référentiel de contrôle de code source central. Cela crée une nouvelle révision du fichier qui est disponible pour les autres utilisateurs. Ce processus s’appelle un archivage.

 Extrayez le fait de demander une copie de travail à partir du référentiel, en informant le référentiel de votre intention de le modifier. Une copie de travail reflète l’état du projet au moment où il est extrait.

 Client un programme qui utilise le système de contrôle de code source. Dans le cadre de cette documentation, il s’agit de l’IDE de Visual Studio.

 Commentez un message décrivant les modifications qu’un utilisateur peut joindre à une révision lors de l’exécution d’une opération de contrôle de code source.

 Conflit dans une situation où deux utilisateurs essaient d’archiver les modifications apportées à la même région du même fichier. En règle générale, une fusion doit être effectuée.

 Répertoire un dossier local côté client est désigné sous le terme de répertoire. Il s’agit de la copie dans laquelle un utilisateur apporte réellement des modifications. Il peut y avoir de nombreuses copies de travail d’un projet donné. en général, chaque développeur possède sa propre copie.

 Obtenir une opération de récupération permet de mettre à jour la copie de travail de l’utilisateur avec la copie du référentiel. Contrairement à une extraction, une opération d’extraction est effectuée lorsque l’utilisateur a simplement besoin de la copie la plus récente, mais n’a pas l’intention d’apporter aucune modification.

 Historique il s’agit généralement d’un résumé de l’ensemble des extractions, archivages, mises à jour, balises et mises en production effectuées dans le référentiel de contrôle de code source.

 L’IDE fait généralement référence à l’environnement de développement intégré de Visual Studio. Toutefois, il peut également faire référence à d’autres environnements clients qui reconnaissent l’API de plug-in de contrôle de code source.

 Fusionnez le processus pendant lequel deux ou plusieurs fichiers de code source sont combinés pour former un nouveau fichier qui incorpore toutes les fonctionnalités des fichiers précédents. Ce concept est essentiel dans le contrôle de version où deux développeurs ou plus travaillent sur des fichiers simultanément.

 Un dossier de contrôle de code source est souvent appelé projet. Cela n’a pas de relation avec les projets ou les solutions dans Visual Studio.

 Plug-in DLL qui fournit une fonctionnalité de contrôle de code source en implémentant l’API de plug-in de contrôle de code source.

 Référentiel copie principale où un système de contrôle de code source stocke l’historique de révision complet d’un projet. Chaque projet a un seul référentiel.

 Révision d’une modification validée dans l’historique d’un fichier ou d’un ensemble de fichiers. Une révision est un instantané dans un projet en perpétuelle évolution.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
