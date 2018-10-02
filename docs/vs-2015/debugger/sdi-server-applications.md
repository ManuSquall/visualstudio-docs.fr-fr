---
title: Applications serveur SDI | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c6ee3ee3a1273c02dd094f89c099230024eabfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508180"
---
# <a name="sdi-server-applications"></a>Applications serveur SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Applications serveur SDI](https://docs.microsoft.com/visualstudio/debugger/sdi-server-applications).  
  
Si vous déboguez une application serveur SDI, vous devez spécifier `/Embedding` ou `/Automation` dans le **arguments de ligne de commande** propriété dans le *projet* boîte de dialogue Pages de propriétés pour C/C++, c#, ou Projets Visual Basic.  
  
 Avec ces arguments de la ligne de commande, le débogueur peut lancer l’application serveur comme si elle était lancée d’un conteneur. Le démarrage du conteneur à partir du Gestionnaire de programmes ou du Gestionnaire de fichiers entraîne l'utilisation par le conteneur de l'instance du serveur démarrée dans le débogueur.  
  
## <a name="finding-the-command-line-arguments-property"></a>Recherche de la propriété Arguments de la ligne de commande  
 Pour accéder à la *projet* boîte de dialogue Pages de propriétés, cliquez sur votre projet dans l’Explorateur de solutions, puis choisissez Propriétés dans le menu contextuel. Pour trouver la propriété Arguments de la ligne de commande, développez la catégorie Propriétés de configuration, puis cliquez sur la page Débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Guide pratique pour déboguer des serveurs COM](../debugger/how-to-debug-com-servers.md)



