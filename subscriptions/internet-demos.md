---
title: Utilisation de clés de produit pour la prise en charge des démonstrations Internet via les services Terminal Server | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Découvrir comment utiliser les clés de produit pour prendre en charge les démonstrations Internet via les services Terminal Server et activer l’accès des Services Bureau à distance
ms.openlocfilehash: 19faa64b7eeaebc1b92ca965f686795b31e00e7e
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493382"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Démonstrations Internet via les services Terminal Server
Avec un abonnement Visual Studio, vous pouvez fournir un accès aux démonstrations Internet de vos programmes aux utilisateurs finaux par le biais des services Terminal Server (Windows Server 2003 ou Windows Server 2008) ou des services Bureau à distance (Windows Server 2008 R2 ou versions ultérieures). Jusqu’à 200 utilisateurs anonymes peuvent ainsi accéder simultanément à votre démonstration. Votre démonstration ne doit pas utiliser de données de production. Les abonnés Visual Studio sont autorisés à démontrer leurs applications aux utilisateurs finaux. Les services Terminal Server ou Bureau à distance sont les seuls moyens pour les utilisateurs finaux sans abonnement Visual Studio d’interagir avec l’application démontrée quand le logiciel est concédé sous licence par le biais d’abonnements Visual Studio.

Cela s’ajoute aux autorisations de développement et de test, qui permettent aux abonnés Visual Studio d’utiliser un nombre illimité de connexions aux services Terminal Server ou Bureau à distance.

## <a name="enabling-rds-access"></a>Activation de l’accès aux services Bureau à distance
Les abonnés Visual Studio peuvent augmenter le nombre d’utilisateurs autorisés à accéder à Windows Server par le biais des services Bureau à distance en entrant une clé de produit fournie sous l’onglet [Clés de produit](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) dans le [portail Abonné](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Pour obtenir une clé de produit, connectez-vous à la page Clés de produit et faites défiler la page jusqu’à la version Windows Server que vous utilisez. Recherchez « Connexions < utilisateur ou appareil > aux services Bureau à distance Windows Server < version > R2 », puis cliquez sur le lien **Demander une clé**. Par exemple, si vous utilisez les services Bureau à distance sur Windows Server 2012 R2 et que votre déploiement utilise des CAL utilisateur, choisissez « Connexions utilisateurs aux services Bureau à distance Windows Server 2012 (50) ».
Cinq clés de chaque type sont disponibles pour Windows Server 2008 R2, et chaque clé prend en charge 20 connexions. Pour Windows Server 2012 R2, quatre clés de chaque type sont disponibles, et chaque clé prend en charge 50 connexions.

## <a name="to-enable-additional-connections-in-windows-server"></a>Pour activer des connexions supplémentaires dans Windows Server :
1. Ouvrez le Gestionnaire de serveur.
2. Ouvrez la liste des serveurs dans le volet de navigation de gauche.
3. Cliquez avec le bouton droit sur votre serveur de licences et choisissez « Installer les licences ».
4. Suivez les étapes de l'Assistant.  Quand vous sélectionnez le type de contrat, choisissez « Pack de licence (version commerciale) », puis entrez la clé de produit obtenue sur le portail MY.

Les utilisateurs finaux peuvent utiliser les services Bureau à distance pour se connecter aux applications si les conditions suivantes sont remplies :
- Les utilisateurs doivent rester anonymes (état non identifié).
- Les connexions doivent se faire par Internet.
- 200 connexions utilisateur au maximum peuvent être utilisées simultanément pour les démonstrations de l’application.
- Les clés de produit permettant d’activer les connexions utilisateur doivent être obtenues par un abonné Visual Studio.

## <a name="next-steps"></a>Étapes suivantes
Si vous avez besoin d’aide pour le déploiement des Services Bureau à distance, consultez la série de blogs en plusieurs parties sur le **déploiement de session des Services Bureau à distance 2012** à l’adresse https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf. 

Si vous avez des questions, consultez le [forum sur les services Bureau à distance Microsoft](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
