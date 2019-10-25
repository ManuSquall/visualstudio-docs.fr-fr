---
title: 'Avertissement de sécurité : le débogueur doit exécuter une commande non approuvée | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0922461c4ca5366e6d1dc215f5711f5566d00ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729751"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avertissement de sécurité : Le débogueur doit exécuter cette commande non approuvée
Cette boîte de dialogue d'avertissement apparaît lorsque vous utilisez le serveur source. Elle indique que la commande que le débogueur a besoin d'exécuter pour obtenir le code source n'est pas dans la liste de commandes de confiance pour le serveur source contenue dans le fichier srcsvr.ini. Si c'est une commande valide, vous pouvez l'ajouter au fichier srcsvr.ini. Sinon, vous ne devez pas l'exécuter. Pour plus d’informations, consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Texte du message
 **Le débogueur doit exécuter cette commande non approuvée pour obtenir le code source du serveur source.**

 **Si le fichier de symboles de débogage (\*.pdb) ne provient pas d’une source connue et approuvée, cette commande peut être non valide ou dangereuse à exécuter.**

 **Souhaitez-vous exécuter cette commande ?**

## <a name="uielement-list"></a>Liste des éléments d’interface
 Commande de zone de texte à partir du fichier. pdb à exécuter.

 Exécutez autoriser l’exécution de la commande.

 N’exécutez pas arrêter l’exécution de la commande et le téléchargement du fichier à partir du serveur source.

## <a name="see-also"></a>Voir aussi
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Serveur source](/windows/desktop/Debug/source-server-and-source-indexing)