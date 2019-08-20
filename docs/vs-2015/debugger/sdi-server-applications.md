---
title: Applications serveur SDI | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148148"
---
# <a name="sdi-server-applications"></a>Applications serveur SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous déboguez une application serveur SDI, vous devez spécifier `/Embedding` ou `/Automation` dans la propriété **Arguments de la ligne de commande** de la boîte de dialogue Pages de propriétés de *projet* pour les projets C/C++, C# ou Visual Basic.  
  
 Avec ces arguments de la ligne de commande, le débogueur peut lancer l'application serveur comme si elle était lancée d'un conteneur. Le démarrage du conteneur à partir du Gestionnaire de programmes ou du Gestionnaire de fichiers entraîne l'utilisation par le conteneur de l'instance du serveur démarrée dans le débogueur.  
  
## <a name="finding-the-command-line-arguments-property"></a>Recherche de la propriété Arguments de la ligne de commande  
 Pour accéder à la boîte de dialogue Pages de propriétés de *projet*, cliquez avec le bouton droit sur votre projet dans l’Explorateur de solutions, puis sélectionnez Propriétés dans le menu contextuel. Pour trouver la propriété Arguments de la ligne de commande, développez la catégorie Propriétés de configuration, puis cliquez sur la page Débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Guide pratique : déboguer des serveurs COM](../debugger/how-to-debug-com-servers.md)
