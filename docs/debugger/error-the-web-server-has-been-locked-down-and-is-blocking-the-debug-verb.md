---
title: Le serveur Web a été verrouillé et bloque le verbe de débogage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e68ab09d7fc398d45a8942c3df4ca0dee5754d2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871207"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Erreur : le serveur Web est verrouillé et bloque l'exécution du verbe DEBUG
L’exécution pas à pas d’une application Web ou d’un service web XML a échoué, car l’outil de verrouillage IIS a été exécuté et URLScan a été installé et activé. Cette condition empêche IIS de recevoir le verbe DEBUG.

 URLScan est un outil de sécurité qui fonctionne conjointement avec l’outil de verrouillage IIS afin de permettre aux administrateurs de sites web IIS de désactiver les fonctionnalités inutiles et de restreindre le type de demandes HTTP traitées par le serveur. En bloquant des demandes HTTP spécifiques, l'outil de sécurité URLScan empêche les demandes potentiellement nuisibles de parvenir au serveur et de provoquer des dommages.

 Si votre application s'exécute sur IIS 6.0 sous Windows Server 2003, il n'est pas nécessaire d'exécuter l'outil de verrouillage IIS puisque IIS 6.0 fournit les mêmes fonctionnalités.

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Pour activer le débogage sur un serveur web sur lequel URLScan est installé

1. Localisez le fichier Urlscan.ini. En général, il se trouve dans un répertoire tel que le suivant :

     C:\WINNT\System32\Inetsrv\urlscan

2. Créez une copie du fichier et nommez-la **Urlscan.old**.

3. Ouvrez la copie originale du fichier Urlscan.ini à l'aide du Bloc-notes ou de l'éditeur de texte de votre choix.

4. Dans Urlscan.ini, localisez la section [AllowVerbs]. Ajoutez DEBUG à la section [AllowVerbs]. Si vous voyez ;DEBUG dans la section [AllowVerbs], supprimez le point-virgule pour supprimer les marques de commentaire du verbe.

5. Recherchez la section [DenyVerbs]. Si DEBUG apparaît dans la section [DenyVerbs], supprimez-le.

6. Enregistrez le fichier .

7. Redémarrez le serveur ou redémarrez IIS.

## <a name="see-also"></a>Voir aussi
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Erreur : le serveur Web n’a pas pu trouver la ressource demandée](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)