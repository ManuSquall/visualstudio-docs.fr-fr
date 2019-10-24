---
title: Débogage de serveur et de conteneur COM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5ed51c72ad7fd64bbdfd0135f53a13bb8c6e4b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745674"
---
# <a name="com-server-and-container-debugging"></a>Débogage de serveurs et de conteneurs COM
Les applications COM effectuent des tâches en dehors du contrôle direct du programmeur. La communication entre les DLL, la fréquence d'utilisation des objets et les opérations du Presse-papiers sont quelques exemples pour lesquels un comportement inattendu peut se produire. Lorsque cela se produit, la première chose à faire est de trouver la source du problème.

 Le débogueur Visual Studio prend en charge le pas à pas dans les conteneurs et les serveurs. Cela inclut la possibilité d'explorer pas à pas les appels de procédure à distance (RPC, Remote Procedure Calls).

## <a name="BKMK_COMServerandContainerintheSameSolution"></a> Débogage d’un serveur COM et d’un conteneur dans la même solution
 Vous pouvez déboguer un serveur et un conteneur COM en utilisant deux projets contenus dans la même solution. Définissez les points d'arrêt appropriés dans chaque projet et commencez le débogage. Lorsque le conteneur fait un appel au serveur qui rencontre un point d'arrêt, le conteneur attend que le code du serveur soit retourné (c'est-à-dire, jusqu'à ce que le débogage soit terminé).

 Le débogage d'un conteneur COM est identique au débogage d'un programme standard. La seule différence se produit lorsque vous déboguez un événement qui génère un rappel (par exemple, le glissement de données sur l'application conteneur). Dans ce cas, vous devez définir un point d'arrêt dans la fonction de rappel.

## <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Débogage d’une application serveur sans informations sur le conteneur
 Si vous ne disposez pas d'informations de débogage pour votre application conteneur ou si vous ne voulez pas les utiliser, le débogage de l'application serveur se passe en trois étapes :

1. Commencez le débogage du serveur comme pour une application normale.

2. Définissez les points d'arrêt voulus.

3. Démarrez l'application conteneur.

## <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Débogage d’une application SDI (Server and Domain Isolation)
 Si vous déboguez une application serveur SDI, vous devez spécifier `/Embedding` ou `/Automation` dans la propriété **Arguments de la ligne de commande** de la boîte de dialogue Pages de propriétés de *projet* pour les projets C/C++, C# ou Visual Basic.

 Avec ces arguments de la ligne de commande, le débogueur peut lancer l'application serveur comme si elle était lancée d'un conteneur. Le démarrage du conteneur à partir du Gestionnaire de programmes ou du Gestionnaire de fichiers entraîne l'utilisation par le conteneur de l'instance du serveur démarrée dans le débogueur.

 Pour accéder à la boîte de dialogue Pages de propriétés de *projet*, cliquez avec le bouton droit sur votre projet dans l’Explorateur de solutions, puis sélectionnez Propriétés dans le menu contextuel. Pour trouver la propriété Arguments de la ligne de commande, développez la catégorie Propriétés de configuration, puis cliquez sur la page Débogage.

## <a name="see-also"></a>Voir aussi

- [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)