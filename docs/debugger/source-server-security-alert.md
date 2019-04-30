---
title: Source d’alerte de sécurité de serveur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 068c5b99e06e180a285b9d72c75c329b10b715af
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407702"
---
# <a name="source-server-security-alert"></a>Alerte de sécurité du serveur source
Lors de l'utilisation du serveur source, n'utilisez que des fichiers de symboles provenant d'un emplacement connu et fiable.

 Cet avertissement apparaît lorsque vous activez le support du serveur source. Les commandes du serveur source sont incorporées dans les fichiers de symboles de débogage (fichiers **\*.pdb**). Assurez-vous que vous savez d'où vos fichiers PDB proviennent.

> [!IMPORTANT]
> Les menaces de sécurité potentielles suivantes doivent être pris en compte lors de l’utilisation du serveur Source : Des commandes arbitraires peuvent être incorporés dans le fichier PDB de l’application, par conséquent, prenez soin de que placer uniquement celles que vous souhaitez exécuter dans le fichier srcsrv.ini. Toute tentative d'exécution d'une commande ne se trouvant pas dans le fichier srcsvr.ini provoque l'apparition d'une boîte de dialogue de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : le débogueur doit exécuter une commande non approuvée](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Aucune validation n’est effectuée sur les paramètres de commande, soyez donc prudent avec les commandes de confiance. Par exemple, vous avez confiance en cmd.exe, mais un utilisateur malveillant a pu spécifier des paramètres qui rendent la commande dangereuse.

## <a name="see-also"></a>Voir aussi
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Serveur source](/windows/desktop/Debug/source-server-and-source-indexing)
