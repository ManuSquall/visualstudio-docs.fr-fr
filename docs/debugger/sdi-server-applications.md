---
title: Applications serveur SDI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9047c9b39bad5f4f790327b5ee65b4de688db9d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="sdi-server-applications"></a>Applications serveur SDI
Si vous déboguez une application serveur SDI, vous devez spécifier `/Embedding` ou `/Automation` dans les **arguments de ligne de commande** propriété dans le *projet* boîte de dialogue Pages de propriétés pour C/C++, c#, ou Projets Visual Basic.  
  
 Avec ces arguments de la ligne de commande, le débogueur peut lancer l’application serveur comme si elle était lancée d’un conteneur. Le démarrage du conteneur à partir du Gestionnaire de programmes ou du Gestionnaire de fichiers entraîne l'utilisation par le conteneur de l'instance du serveur démarrée dans le débogueur.  
  
## <a name="finding-the-command-line-arguments-property"></a>Recherche de la propriété Arguments de la ligne de commande  
 Pour accéder à la *projet* boîte de dialogue Pages de propriétés, avec le bouton droit de votre projet dans l’Explorateur de solutions, puis choisissez Propriétés dans le menu contextuel. Pour trouver la propriété Arguments de la ligne de commande, développez la catégorie Propriétés de configuration, puis cliquez sur la page Débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Guide pratique pour déboguer des serveurs COM](../debugger/how-to-debug-com-servers.md)