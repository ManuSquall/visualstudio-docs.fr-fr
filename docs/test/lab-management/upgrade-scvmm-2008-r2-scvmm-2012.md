---
title: "Mettre à niveau SCVMM 2008 R2 vers SCVMM 2012 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.assetid: 5be92444-c701-43c7-8b2a-77df8e02bc27
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: b7874e87ea81bf6b0818b4b9eefba0f86bd2a2e2
ms.contentlocale: fr-fr
ms.lasthandoff: 06/02/2017

---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Mettre à niveau SCVMM 2008 R2 vers SCVMM 2012

Lab Management pour Team Foundation Server prend en charge SCVMM 2008 R2 et SCVMM 2012. Si vous mettez à niveau Team Foundation Server 2013 vers Team Foundation Server 2015 et que vous prévoyez de mettre à niveau SCVMM 2008 R2 vers SCVMM 2012, nous vous recommandons de mettre à niveau vers SCVMM 2012 après avoir mis à niveau vers Team Foundation Server 2015. Cette rubrique décrit comment mettre à niveau SCVMM 2008 R2 vers SCVMM 2012 quand vous utilisez Lab Management sur Team Foundation Server 2015.
Lab Management **ne prend pas** en charge SCVMM 2016. 

**Important :** Quand vous mettez à jour SCVMM, certaines étapes provoquent une indisponibilité temporaire de votre serveur Team Foundation Server. Vous pouvez trouver ces étapes ci-dessous.

## <a name="upgrading-to-scvmm-2012"></a>Mise à niveau vers SCVMM 2012

1. Utiliser l'installateur SCVMM 2012 pour mettre à niveau SCVMM 2008 R2 Server vers SCVMM 2012 Server.

1. Mettez à jour les agents SCVMM sur vos hôtes et partages de bibliothèques.

1. Utilisez la Console d'Administration SCVMM pour vérifier que tous les composants SCVMM fonctionnent.

1. Installez la Console d’Administration SCVMM 2012 sur chaque machine des couches Application de votre serveur Team Foundation Server.

1. Utilisez la commande **iisreset** pour redémarrer le service web Team Foundation Server. Redémarrez l’agent de travail Team Foundation Server.

   **Attention :** Cette étape interrompt les services sur votre serveur Team Foundation Server.

1. Mettez à jour les données et les modèles dans chaque base de données de collection de projet pour assurer la compatibilité avec SCVMM. 
   2012.

   Ouvrez une invite de commandes avec élévation de privilèges sur votre serveur Team Foundation Server et entrez la commande suivante :

   **C:\\Program Files\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   Quand vous utilisez la commande **upgradeSCVMM**, Team Foundation Server crée un nouvel objet de modèle sur votre serveur SCVMM pour chaque projet d’équipe qui utilise ce modèle. Ceci assure que vos modèles sont mis à jour pour être compatible avec SCVMM 2012 sans perdre de données. Néanmoins, lorsque les nouveaux modèles sont crées, le projet d’équipe est joint au nom du modèle.

   **Attention :**  
   Si le nouveau nom du modèle comporte plus de 64 caractères, cela entraîne un échec SCVMM. Pour résoudre l'erreur, vous devez attribuer un nom plus court à vos modèles. Si vous rencontrez d’autres erreurs ou avertissements quand vous exécutez cette commande, consultez la section suivante pour les résoudre. Si vous ne rencontrez pas d'erreur ni d'avertissement, votre mise à niveau est terminée et vous pouvez commencer à utiliser les environnements SCVMM avec Lab Management.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Résolution d'erreurs et d'avertissements à l'aide de la commande upgradeSCVMM

Après avoir utilisé la commande **upgradeSCVMM**, vous devez résoudre toutes les erreurs et les avertissements que vous recevez, puis réexécuter la commande avant de pouvoir utiliser Lab Management. La commande **upgradeSCVMM** génère un fichier journal qui contient des informations sur les erreurs et avertissements que vous rencontrez. L’emplacement du fichier journal est affiché quand vous exécutez la commande **upgradeSCVMM**.

**Échec SCVMM :** si vous recevez une erreur liée à un échec SCVMM, utilisez votre historique des travaux SCVMM pour obtenir des informations supplémentaires sur l’erreur. Après avoir résolu l’erreur dans SCVMM, réexécutez la commande **upgradeSCVMM**.

## <a name="see-also"></a>Voir aussi

* [Modification de configurations Lab Management existantes](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)

