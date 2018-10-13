---
title: Source d’alerte de sécurité de serveur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f75ae71cb03e4811e5fa0599bd1ee51371c7891
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230098"
---
# <a name="source-server-security-alert"></a>Alerte de sécurité du serveur source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de l'utilisation du serveur source, n'utilisez que des fichiers de symboles provenant d'un emplacement connu et fiable.  
  
 Cet avertissement apparaît lorsque vous activez le support du serveur source. Les commandes du serveur source sont incorporées dans les fichiers de symboles de débogage (fichiers PDB). Assurez-vous que vous savez d'où vos fichiers PDB proviennent.  
  
> [!IMPORTANT]
>  Tenez compte des risques potentiels suivants sur la sécurité lorsque vous utilisez le serveur source : comme des commandes arbitraires peuvent s'insérer dans le fichier PDB de l'application, veillez à ne mettre dans le fichier srcsrv.ini que celles que vous souhaitez exécuter. Toute tentative d'exécution d'une commande ne se trouvant pas dans le fichier srcsvr.ini provoque l'apparition d'une boîte de dialogue de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : débogueur Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Aucune validation n’est effectuée sur les paramètres de commande, soyez prudent avec les commandes approuvées. Par exemple, vous avez confiance en cmd.exe, mais un utilisateur malveillant a pu spécifier des paramètres qui rendent la commande dangereuse.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Serveur source](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)



