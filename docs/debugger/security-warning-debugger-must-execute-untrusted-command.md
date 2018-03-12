---
title: "Avertissement de sécurité : Le débogueur doit exécuter une commande non approuvée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8749cea92e0ee16a14ecbaa3cc8732131c5a7f51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avertissement de sécurité : Le débogueur doit exécuter cette commande non approuvée
Cette boîte de dialogue d'avertissement apparaît lorsque vous utilisez le serveur source. Elle indique que la commande que le débogueur a besoin d'exécuter pour obtenir le code source n'est pas dans la liste de commandes de confiance pour le serveur source contenue dans le fichier srcsvr.ini. Si c'est une commande valide, vous pouvez l'ajouter au fichier srcsvr.ini. Sinon, vous ne devez pas l'exécuter. Pour plus d’informations, consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Texte du message  
 **Le débogueur doit exécuter cette commande non approuvée pour obtenir le code source à partir du serveur source.**  
  
 **Si le débogage de fichier de symboles (\*.pdb) est non à partir d’une source connue et approuvée, cette commande peut être non valide ou dangereuse à exécuter.**  
  
 **Voulez-vous exécuter cette commande ?**  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 Zone de texte  
 Commande du fichier .pdb à exécuter.  
  
 Run  
 Permet l'exécution de la commande.  
  
 Ne pas exécuter  
 Arrête l'exécution de la commande et le téléchargement du fichier à partir du serveur source.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifiez les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Serveur source](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)