---
title: Alerte de sécurité du serveur source | Microsoft Docs
description: En savoir plus sur l’avertissement d’alerte de sécurité du serveur source dans le débogueur Visual Studio. Tenez compte des menaces de sécurité potentielles lors de l’utilisation du serveur source.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bf62abb91411048f46bfe7240074bd86c119bcd4
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149116"
---
# <a name="source-server-security-alert"></a>Alerte de sécurité du serveur source
Lors de l'utilisation du serveur source, n'utilisez que des fichiers de symboles provenant d'un emplacement connu et fiable.

 Cet avertissement apparaît lorsque vous activez le support du serveur source. Les commandes du serveur source sont incorporées dans les fichiers de symboles de débogage (fichiers **\* . pdb** ). Assurez-vous que vous savez d'où vos fichiers PDB proviennent.

> [!IMPORTANT]
> Tenez compte des risques potentiels suivants sur la sécurité lorsque vous utilisez le serveur source : comme des commandes arbitraires peuvent s'insérer dans le fichier PDB de l'application, veillez à ne mettre dans le fichier srcsrv.ini que celles que vous souhaitez exécuter. Toute tentative d'exécution d'une commande ne se trouvant pas dans le fichier srcsvr.ini provoque l'apparition d'une boîte de dialogue de confirmation. Pour plus d'informations, consultez [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Aucune validation n’est effectuée sur les paramètres de commande, soyez donc prudent avec les commandes de confiance. Par exemple, vous avez confiance en cmd.exe, mais un utilisateur malveillant a pu spécifier des paramètres qui rendent la commande dangereuse.

## <a name="see-also"></a>Voir aussi
- [Spécifier les fichiers de symboles (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Serveur source](/windows/desktop/Debug/source-server-and-source-indexing)
