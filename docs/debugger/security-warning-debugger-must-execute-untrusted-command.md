---
title: 'Avertissement de sécurité : Le débogueur doit exécuter une commande non approuvée | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e421521bd40ff4369433b0a0c3c323579e36125
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855610"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avertissement de sécurité : le débogueur doit exécuter une commande non approuvée
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
 [Serveur source](/windows/desktop/Debug/source-server-and-source-indexing)