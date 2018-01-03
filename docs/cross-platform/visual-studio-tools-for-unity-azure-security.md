---
title: "Procédure pas à pas de sécurité Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 1ffb0c57329a8453208978cee69daa771d8ee0e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Mettre à jour le magasin de certificats de sécurité Mono d’Unity

Mono d’Unity est fourni avec un magasin de certificats vide et n’approuve par conséquent aucun site. Vous pouvez en savoir plus à ce sujet sur le [Forum aux questions sur la sécurité Mono](http://www.mono-project.com/docs/faq/security/).

Pour pouvoir vous connecter à Azure sans ignorer TLS/SSL, le magasin de certificats Mono d’Unity doit être mis à jour.

## <a name="using-mozroots-to-install-certificates"></a>Utilisation de mozroots pour installer des certificats

L’outil mozroots est inclus dans Mono. Il télécharge et installe la liste de certificats racines de Mozilla.

1. Ouvrez le terminal d’invite de commandes.

2. Naviguez dans le terminal jusqu’au répertoire **C:\Program Files\Unity\Editor\Data\MonoBleedingEdge\bin>**. L’emplacement exact peut différer selon l’endroit où vous avez installé Unity sur votre ordinateur local.

3. Tapez la commande suivante, puis appuyez sur **Entrée** pour l’exécuter :

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Vous devez obtenir la sortie suivante (même si le nombre de certificats ajoutés peut varier) :

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. Vous devez désormais être en mesure d’exécuter l’exemple de projet sans recevoir d’erreurs TLS.

## <a name="next-step"></a>Étape suivante

* [Tester la connexion du client](visual-studio-tools-for-unity-azure-connection.md)
