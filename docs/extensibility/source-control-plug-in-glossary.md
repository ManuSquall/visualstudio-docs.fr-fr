---
title: Glossaire de plug-in de contrôle de source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fdd9cd8ee037b376b086def1464888f1ae6e11f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826836"
---
# <a name="source-control-plug-in-glossary"></a>Glossaire de plug-in de contrôle de code source
L’utiles termes et définitions ci-après se rapportent à la documentation du SDK de plug-in de contrôle de code Source.  
  
## <a name="definitions"></a>Définitions  
 Archivage  
 Lorsqu’un utilisateur apporte des modifications à une copie de travail, un utilisateur doit envoyer les modifications à partir de la copie de travail dans le référentiel de contrôle source centrale. Cette opération crée une nouvelle révision du fichier qui est disponible à d’autres utilisateurs. Ce processus est appelé un archivage.  
  
 Extraction  
 Consistant à demander une copie de travail à partir du référentiel, informant le référentiel de votre intention de le modifier. Une copie de travail reflète l’état du projet au moment où qu'il est extrait.  
  
 Client  
 Un programme qui utilise le système de contrôle de code source. Pour les besoins de cette documentation, il est l’IDE Visual Studio.  
  
 Commentaire  
 Un message décrivant les modifications un utilisateur peut attacher à une révision lorsqu’une opération de contrôle de code source est effectuée.  
  
 Conflit  
 Se produit lorsque deux utilisateurs essaient d’archiver les modifications apportées à la même région du même fichier. En règle générale, une fusion doit être effectuée.  
  
 Répertoire  
 Un dossier local côté client est désigné en tant que répertoire. Il s’agit de la copie dans laquelle un utilisateur apporte réellement des modifications. Il peut y avoir de nombreuses copies de travail d’un projet donné ; en règle générale, chaque développeur a sa propre copie.  
  
 Télécharger  
 Une opération get apporte la copie de travail utilisateur à jour avec la copie du référentiel. Contrairement à une extraction, une opération get est effectuée lorsque l’utilisateur a besoin de la dernière copie simplement mais prévoit d’apporter aucune modification.  
  
 Historique  
 Il est généralement un résumé de toutes les extractions, archivages, les mises à jour, des balises et mises en production effectuées dans le référentiel de contrôle source.  
  
 IDE  
 Se réfère généralement à l’environnement de développement intégré Visual Studio. Toutefois, il peut également faire référence à d’autres environnements de client qui reconnaissent l’API de plug-in de contrôle de Source.  
  
 Fusionner  
 Le processus au cours de la source à laquelle deux ou plusieurs fichiers de code sont combinées pour former un nouveau fichier qui incorpore toutes les fonctionnalités à partir de fichiers précédents. Ce concept est essentiel dans le contrôle de version dans laquelle deux ou plusieurs développeurs travaillent sur des fichiers simultanément.  
  
 Projet  
 Un dossier de contrôle de code source est souvent appelé un projet. Cela n’a pas aucune relation avec les projets ou des solutions dans Visual Studio.  
  
 Plug-in  
 Une DLL qui fournit des fonctionnalités de contrôle de code source en implémentant l’API de plug-in de contrôle de Source.  
  
 Référentiel  
 La copie principale où une source de système de contrôle stocke l’historique de révision complète d’un projet. Chaque projet possède un seul référentiel.  
  
 Révision  
 Une modification validée dans l’historique d’un fichier ou un ensemble de fichiers. Une révision est un instantané dans un projet en constante évolution.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)