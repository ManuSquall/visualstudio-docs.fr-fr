---
title: Glossaire du plug-in de contrôle de code source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160602"
---
# <a name="source-control-plug-in-glossary"></a>Glossaire de plug-in de contrôle de code source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les termes et définitions utiles suivants concernent la documentation du kit de développement logiciel (SDK) du plug-in de contrôle de code source.  
  
## <a name="definitions"></a>Définitions  
 Archivage  
 Lorsqu’un utilisateur apporte des modifications à une copie de travail, il doit envoyer les modifications à partir de la copie de travail dans le référentiel de contrôle de code source central. Cela crée une nouvelle révision du fichier qui est disponible pour les autres utilisateurs. Ce processus s’appelle un archivage.  
  
 Checkout  
 Action de demander une copie de travail à partir du référentiel, en informant le dépôt de votre intention de le modifier. Une copie de travail reflète l’état du projet au moment où il est extrait.  
  
 Client  
 Programme qui utilise le système de contrôle de code source. Dans le cadre de cette documentation, il s’agit de l’IDE de Visual Studio.  
  
 Commentaire  
 Message décrivant les modifications qu’un utilisateur peut joindre à une révision lors de l’exécution d’une opération de contrôle de code source.  
  
 Conflit  
 Situation dans laquelle deux utilisateurs essaient d’archiver les modifications apportées à la même région du même fichier. En règle générale, une fusion doit être effectuée.  
  
 Répertoire  
 Un dossier local côté client est désigné sous le terme de répertoire. Il s’agit de la copie dans laquelle un utilisateur apporte réellement des modifications. Il peut y avoir de nombreuses copies de travail d’un projet donné. en général, chaque développeur possède sa propre copie.  
  
 Obtenir  
 Une opération d’extraction met à jour la copie de travail de l’utilisateur avec la copie du référentiel. Contrairement à une extraction, une opération d’extraction est effectuée lorsque l’utilisateur a simplement besoin de la copie la plus récente, mais n’a pas l’intention d’apporter aucune modification.  
  
 Historique  
 Il s’agit généralement d’un résumé de l’ensemble des extractions, archivages, mises à jour, balises et mises en production effectuées dans le référentiel de contrôle de code source.  
  
 IDE  
 Fait généralement référence à l’environnement de développement intégré de Visual Studio. Toutefois, il peut également faire référence à d’autres environnements clients qui reconnaissent l’API de plug-in de contrôle de code source.  
  
 Fusionner  
 Processus au cours duquel deux ou plusieurs fichiers de code source sont combinés pour former un nouveau fichier qui incorpore toutes les fonctionnalités des fichiers précédents. Ce concept est essentiel dans le contrôle de version où deux développeurs ou plus travaillent sur des fichiers simultanément.  
  
 Project  
 Un dossier de contrôle de code source est souvent appelé projet. Cela n’a pas de relation avec les projets ou les solutions dans Visual Studio.  
  
 Plug-in  
 DLL qui fournit des fonctionnalités de contrôle de code source en implémentant l’API de plug-in de contrôle de code source.  
  
 Référentiel  
 Copie principale dans laquelle un système de contrôle de code source stocke l’historique de révision complet d’un projet. Chaque projet a un seul référentiel.  
  
 Révision  
 Modification validée dans l’historique d’un fichier ou d’un ensemble de fichiers. Une révision est un instantané dans un projet en perpétuelle évolution.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
