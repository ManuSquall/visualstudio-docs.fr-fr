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
ms.openlocfilehash: af216023b1a157136f86f0ca8527a8b433b0a34b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719143"
---
# <a name="source-server-security-alert"></a>Alerte de sécurité du serveur source
Lors de l'utilisation du serveur source, n'utilisez que des fichiers de symboles provenant d'un emplacement connu et fiable.

 Cet avertissement apparaît lorsque vous activez le support du serveur source. Les commandes du serveur source sont incorporées dans les fichiers de symboles de débogage (fichiers **\*.pdb**). Assurez-vous que vous savez d'où vos fichiers PDB proviennent.

> [!IMPORTANT]
>  Tenez compte des risques potentiels suivants sur la sécurité lorsque vous utilisez le serveur source : comme des commandes arbitraires peuvent s'insérer dans le fichier PDB de l'application, veillez à ne mettre dans le fichier srcsrv.ini que celles que vous souhaitez exécuter. Toute tentative d'exécution d'une commande ne se trouvant pas dans le fichier srcsvr.ini provoque l'apparition d'une boîte de dialogue de confirmation. Pour plus d'informations, consultez [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Aucune validation n’est effectuée sur les paramètres de commande, soyez donc prudent avec les commandes de confiance. Par exemple, vous avez confiance en cmd.exe, mais un utilisateur malveillant a pu spécifier des paramètres qui rendent la commande dangereuse.

## <a name="see-also"></a>Voir aussi
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Serveur source](/windows/desktop/Debug/source-server-and-source-indexing)
