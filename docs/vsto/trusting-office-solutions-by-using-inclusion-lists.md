---
title: Approuver des solutions Office à l’aide de listes d’inclusion
description: Découvrez comment les listes d’inclusion permettent aux utilisateurs d’accorder une confiance aux solutions Office signées avec un certificat qui identifie le serveur de publication.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3bb5c111b4c75298ee55bc64dfbb2d0dd4b6c8b5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527466"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Approuver des solutions Office à l’aide de listes d’inclusion
  Les listes d’inclusion permettent aux utilisateurs d’approuver des solutions Office signées avec un certificat qui identifie l’éditeur. Elles sont propres à l’utilisateur et elles peuvent servir aux personnalisations au niveau du document et aux compléments VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Quand un utilisateur démarre une solution Office qui n’a pas été approuvée pour lui, il est invité à prendre une décision en matière de sécurité avec une invite d’approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Si l’utilisateur décide d’approuver la solution, la personnalisation s’exécute et il ne reçoit plus d’invite au prochain démarrage de la solution.

## <a name="inclusion-list-and-windows-installer"></a>Liste d’inclusion et Windows Installer
 L’installation de solutions Office dans le répertoire *Program Files* à l’aide de Windows Installer nécessite des droits d’administrateur. Pour les solutions Office dans le répertoire *Program Files* , le Visual Studio Tools pour Office Runtime ne vérifie plus la liste d’inclusion car les solutions Office ont déjà reçu l’autorisation FullTrust.

## <a name="clickonce-trust-prompt"></a>Invite d’approbation ClickOnce
 À l’aide de l’implémentation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] des solutions Office, les administrateurs peuvent configurer le niveau d’invite d’approbation pour autoriser les invites, désactiver les invites ou exiger un certificat de confiance. Cette configuration s’effectue à l’aide d’une clé de Registre qui contrôle l’accès à la liste d’inclusion.

 Si l’invite est désactivée, seules les solutions qui possèdent un certificat de confiance connu peuvent être installées. Si le niveau d’invite défini est Authenticode requis, la solution doit être signée avec un certificat émis par une autorité connue, mais elle ne requiert pas un certificat lié à une autorité racine approuvée (un certificat de confiance). Si l’invite est autorisée, la solution peut être signée avec un certificat dont l’identité est inconnue. Dans ce scénario, la décision d’approbation est soumise à l’utilisateur final et un certificat temporaire suffit pour installer une solution.

 Pour plus d’informations, consultez [Comment : configurer la sécurité de la liste d’inclusion et le](../vsto/how-to-configure-inclusion-list-security.md) tableau 2, intitulé effets du lancement de la valeur de clé de registre de niveau d’invite, dans configurer les [éditeurs approuvés ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Structure de la liste d’inclusion
 Une entrée de liste d’inclusion valide comporte deux parties : un chemin vers le manifeste de déploiement et la clé publique utilisée pour signer la solution. Une fois qu’une solution est ajoutée à la liste d’inclusion, elle est considérée comme approuvée. Quand la solution Office s’exécute, l’application Office compare la clé publique figurant dans la liste d’inclusion à la clé de signature figurant dans le manifeste de déploiement pour vérifier que la solution qui est en cours d’exécution est identique à la version d’origine approuvée.

## <a name="see-also"></a>Voir aussi
- [Accorder un niveau de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
