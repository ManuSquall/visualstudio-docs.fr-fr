---
title: 'Procédure : Afficher les Documents de Script | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3592056fdde7756f3fbe63d0dc5d86782fdf9a8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867724"
---
# <a name="how-to-view-script-documents"></a>Procédure : afficher les documents de script
Dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les fichiers de script côté client générés depuis un script côté serveur s'affichaient dans la fenêtre Explorateur de scripts. La fenêtre Explorateur de scripts était souvent masquée et la disponibilité du script côté client n'était pas toujours évidente.  
  
 Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], les fichiers de script côté client générés depuis un script côté serveur s'affichent dans l'Explorateur de solutions visible par défaut. La fenêtre Explorateur de scripts a été supprimée.  
  
 Les fichiers de script côté client sont visibles uniquement lorsque vous êtes en mode débogage ou en mode arrêt. Ils apparaissent dans le nœud **Documents de script**.  
  
 Les fichiers de script côté serveur sont toujours visibles. Ils sont affichés dans le nœud **\<Chemin du site web>**. Le nom du nœud ressemble à cet exemple : `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Pour afficher un document de script côté serveur  
  
1.  Dans l’**Explorateur de solutions**, ouvrez le nœud **\<Chemin du site web>**.  
  
2.  Double-cliquez sur le fichier de script que vous souhaitez afficher.  
  
     Le fichier de script côté serveur s'ouvre dans une fenêtre source.  
  
### <a name="to-view-a-client-side-script-document"></a>Pour afficher un document de script côté client  
  
1.  Dans l’**Explorateur de solutions**, ouvrez le nœud **Documents de script**.  
  
2.  Double-cliquez sur le fichier de script que vous souhaitez afficher.  
  
     Le fichier de script côté client s'ouvre dans une fenêtre source.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)