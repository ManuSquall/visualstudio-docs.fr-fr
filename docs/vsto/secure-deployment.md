---
title: "Déploiement sécurisé | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f52c6d26132490defafdf87639e0f1731ea90640
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="secure-deployment"></a>Déploiement sécurisé
  Lorsque vous créez une solution Office, votre ordinateur de développement est automatiquement mis à jour pour permettre au code dans votre projet à exécuter. Toutefois, lorsque vous déployez votre solution, vous devez fournir une preuve sur laquelle baser la décision d’approbation en signant la solution avec un certificat ou en utilisant le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation. Pour plus d’informations, consultez [l’octroi de confiance à des Solutions Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Pour les personnalisations au niveau du document, si vous déployez le document sur un emplacement réseau, vous devez également ajouter l’emplacement du document à la liste des emplacements approuvés dans le centre de gestion de l’application Office. Pour plus d’informations sur la façon de définir les autorisations du document sur l’utilisateur final ordinateurs, consultez [l’octroi de confiance à des Documents](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Empêche l’exécution de Code des Solutions Office  
 Les administrateurs peuvent utiliser le Registre pour empêcher que toutes les solutions Office en cours d’exécution sur un ordinateur. Lorsqu’une solution Office qui a des extensions de code managé est ouvert, Visual Studio Tools pour la vérification de Office runtime si une entrée avec le nom `Disabled` existe sous une des clés de Registre suivantes sur l’ordinateur :  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Pour empêcher les solutions Office à partir de l’exécution du code, créez un `Disabled` entrée sous un ou deux de ces clés de Registre et spécifiez l’une des valeurs pour les types de données suivants `Disabled`:  
  
-   REG_SZ ou REG_EXPAND_SZ est définie sur n’importe quelle chaîne autre que « 0 » (zéro).  
  
-   REG_DWORD qui est définie à toute valeur autre que 0 (zéro).  
  
 Pour activer les solutions Office d’exécuter du code, définissez à la fois de la `Disabled` entrées à 0 (zéro), ou supprimez les entrées de Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Préparation des ordinateurs pour exécuter ou héberger des Solutions Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sécurisation de solutions Office](../vsto/securing-office-solutions.md)  
  
  