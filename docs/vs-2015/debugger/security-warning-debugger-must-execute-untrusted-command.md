---
title: 'Avertissement de sécurité : Le débogueur doit exécuter une commande non approuvée | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c57a9ce2b5a1ce9de0ffadb4b623ef3a33b8e9ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948906"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avertissement de sécurité : le débogueur doit exécuter une commande non approuvée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue d'avertissement apparaît lorsque vous utilisez le serveur source. Elle indique que la commande que le débogueur a besoin d'exécuter pour obtenir le code source n'est pas dans la liste de commandes de confiance pour le serveur source contenue dans le fichier srcsvr.ini. Si c'est une commande valide, vous pouvez l'ajouter au fichier srcsvr.ini. Sinon, vous ne devez pas l'exécuter. Pour plus d’informations, consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Texte du message  
 **Le débogueur doit exécuter cette commande non approuvée pour obtenir le code source du serveur source.**  
  
 **Si le fichier de symboles de débogage (\*.pdb) ne provient pas d’une source connue et approuvée, cette commande peut être non valide ou dangereuse à exécuter.**  
  
 **Souhaitez-vous exécuter cette commande ?**  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 Zone de texte  
 Commande du fichier .pdb à exécuter.  
  
 Exécuter  
 Permet l'exécution de la commande.  
  
 Ne pas exécuter  
 Arrête l'exécution de la commande et le téléchargement du fichier à partir du serveur source.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Serveur source](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
