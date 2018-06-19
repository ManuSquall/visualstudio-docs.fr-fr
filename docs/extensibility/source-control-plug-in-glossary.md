---
title: Glossaire de plug-in de contrôle de source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: ccfd4cbbbca86d3b6e93d9998410c5dea117328d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139024"
---
# <a name="source-control-plug-in-glossary"></a>Glossaire plug-in de contrôle de code source
Les termes utiles suivants et les définitions se rapportent à la documentation du SDK du plug-in de contrôle de Source.  
  
## <a name="definitions"></a>Définitions  
 Archivage  
 Lorsqu’un utilisateur apporte des modifications à une copie de travail, un utilisateur doit envoyer les modifications à partir de la copie de travail dans le référentiel de contrôle source centrale. Cette opération crée une nouvelle révision du fichier qui est disponible à d’autres utilisateurs. Ce processus est appelé un archivage.  
  
 Extraction  
 Le fait de demander une copie de travail à partir du référentiel, qui informe le référentiel de votre intention de le modifier. Une copie de travail reflète l’état du projet au moment où qu'il est extrait.  
  
 Client  
 Un programme qui utilise le système de contrôle de code source. Dans cette documentation, il s’agit de l’IDE de Visual Studio.  
  
 Commentaire  
 Message décrivant les modifications un utilisateur peut attacher à une révision lorsqu’une opération de contrôle de code source est effectuée.  
  
 Conflit  
 Se produit lorsque deux utilisateurs tentent d’archiver des modifications apportées à la même région du même fichier. En règle générale, une fusion doit être effectuée.  
  
 Répertoire  
 Un dossier local côté client correspond à un répertoire. Il s’agit de la copie dans lequel un utilisateur apporte réellement des modifications. Il peut y avoir de nombreuses copies de travail d’un projet donné. en règle générale, chaque développeur a sa propre copie.  
  
 Télécharger  
 Une opération get met la copie de travail de l’utilisateur à jour avec la copie du référentiel. Contrairement à une extraction, une commande get est effectué lorsque l’utilisateur a besoin de la dernière copie simplement mais prévoit de n’apporter aucune modification.  
  
 Historique  
 Il s’agit d’un résumé de toutes les extractions, archivages, les mises à jour, des balises et versions dans le référentiel de contrôle de code source.  
  
 IDE  
 Désigne généralement l’environnement de développement intégré Visual Studio. Toutefois, il peut également faire référence à d’autres environnements de client qui reconnaissent l’API de plug-in de contrôle de Source.  
  
 Fusionner  
 Le processus pendant les deux ou plusieurs sources de fichiers de code sont combinées pour former un nouveau fichier qui incorpore toutes les fonctionnalités à partir de fichiers précédents. Ce concept est fondamental dans le contrôle de version dans laquelle deux ou plusieurs développeurs travaillent simultanément sur des fichiers.  
  
 Projet  
 Un dossier de contrôle de code source est communément appelée un projet. Cela n’a pas de relation avec des projets ou des solutions dans Visual Studio.  
  
 Plug-in  
 Une DLL qui fournit des fonctionnalités de contrôle de code source en mettant en œuvre de l’API de plug-in de contrôle de Source.  
  
 Référentiel  
 La copie principale, où une contrôle de code source système stocke l’historique de révision complète d’un projet. Chaque projet possède un seul référentiel.  
  
 Révision  
 Une modification validée dans l’historique d’un fichier ou un ensemble de fichiers. Une révision est un instantané dans un projet en constante évolution.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)