---
title: "Glossaire de plug-in de contrôle de source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 11
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
ms.openlocfilehash: 251e104336d19e9f88926e5ca75a85330039fbe8
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-in-glossary"></a>Glossaire du plug-in de contrôle de code source
L’utiles termes et définitions suivants se rapportent à la documentation du SDK du plug-in de contrôle de Source.  
  
## <a name="definitions"></a>Définitions  
 Archivage  
 Lorsqu’un utilisateur apporte des modifications à une copie de travail, un utilisateur doit envoyer les modifications à partir de la copie de travail dans le référentiel de contrôle source centrale. Cela crée une nouvelle version du fichier qui est disponible à d’autres utilisateurs. Ce processus est appelé un archivage.  
  
 Extraction  
 Action consistant à demander une copie de travail à partir du référentiel, qui informe le référentiel de votre intention de le modifier. Une copie de travail reflète l’état du projet au moment où qu'il est extrait.  
  
 Client  
 Un programme qui utilise le système de contrôle de code source. Dans cette documentation, il est de l’IDE de Visual Studio.  
  
 Commentaire  
 Message décrivant les modifications que l’utilisateur peut attacher à une révision lorsqu’une opération de contrôle de code source est effectuée.  
  
 Conflit  
 Se produit lorsque deux utilisateurs essaient d’archiver les modifications apportées à la même région d’un même fichier. En règle générale, une fusion doit être effectuée.  
  
 Répertoire  
 Un dossier local côté client correspond à un répertoire. Il s’agit de la copie dans laquelle un utilisateur effectue réellement les changements. Il peut y avoir de nombreuses copies de travail d’un projet donné. Généralement, chaque développeur possède sa propre copie.  
  
 Obtenir  
 Une opération get apporte la copie de travail de l’utilisateur à jour la copie du référentiel. Contrairement à une extraction, une opération get est effectuée lorsque l’utilisateur a besoin de la dernière copie simplement mais prévoit de n’apporter aucune modification.  
  
 Historique  
 Il s’agit d’un résumé de toutes les extractions, archivages, les mises à jour, des balises et versions dans le référentiel de contrôle de code source.  
  
 IDE  
 Se réfère généralement à l’environnement de développement intégré Visual Studio. Toutefois, il peut également faire référence à d’autres environnements client qui reconnaissent l’API de plug-in de contrôle de Source.  
  
 Fusionner  
 Le processus pendant les deux ou plusieurs sources de fichiers de code sont combinés pour former un nouveau fichier qui intègre toutes les fonctionnalités des fichiers précédents. Ce concept est essentiel dans le contrôle de version dans laquelle deux ou plusieurs développeurs travaillent sur les fichiers simultanément.  
  
 Projet  
 Un dossier de contrôle de code source est souvent appelé un projet. Cela n’a pas de relation avec des projets ou des solutions dans Visual Studio.  
  
 Plug-in  
 Une DLL qui fournit des fonctionnalités de contrôle de code source par l’implémentation de l’API de plug-in de contrôle de Source.  
  
 Référentiel  
 La copie principale, où une contrôle du code source système stocke l’historique de révision complète d’un projet. Chaque projet possède un seul référentiel.  
  
 Révision  
 Une modification validée dans l’historique d’un fichier ou un ensemble de fichiers. Une révision est un instantané dans un projet en constante évolution.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
