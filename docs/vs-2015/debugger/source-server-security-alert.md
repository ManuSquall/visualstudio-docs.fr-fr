---
title: Source d’alerte de sécurité de serveur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699323"
---
# <a name="source-server-security-alert"></a>Alerte de sécurité du serveur source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de l'utilisation du serveur source, n'utilisez que des fichiers de symboles provenant d'un emplacement connu et fiable.  
  
 Cet avertissement apparaît lorsque vous activez le support du serveur source. Les commandes du serveur source sont incorporées dans les fichiers de symboles de débogage (fichiers PDB). Assurez-vous que vous savez d'où vos fichiers PDB proviennent.  
  
> [!IMPORTANT]
> Les menaces de sécurité potentielles suivantes doivent être pris en compte lors de l’utilisation du serveur Source : Des commandes arbitraires peuvent être incorporés dans le fichier PDB de l’application, par conséquent, prenez soin de que placer uniquement celles que vous souhaitez exécuter dans le fichier srcsrv.ini. Toute tentative d'exécution d'une commande ne se trouvant pas dans le fichier srcsvr.ini provoque l'apparition d'une boîte de dialogue de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : Le débogueur doit exécuter une commande non approuvée](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Aucune validation n’est effectuée sur les paramètres de commande, soyez prudent avec les commandes approuvées. Par exemple, vous avez confiance en cmd.exe, mais un utilisateur malveillant a pu spécifier des paramètres qui rendent la commande dangereuse.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Serveur source](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
