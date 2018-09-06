---
title: 'Comment : signer des solutions Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 161c175b6bb37ece93559f0378bbaf8e5e16d170
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776131"
---
# <a name="how-to-sign-office-solutions"></a>Comment : signer des solutions Office
  Si vous vous connectez à une solution, vous pouvez accorder une confiance à la solution en utilisant le certificat en tant que preuve. Vous pouvez utiliser le même certificat pour plusieurs solutions, et toutes les solutions seront approuvées avec aucune mise à jour de stratégie de sécurité supplémentaire.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si vous modifiez manuellement l’application et manifestes de déploiement à l’aide de la Manifest Generation and Editing Tool (*mage.exe* et *mageui.exe*), vous devez resigner les manifestes avant de pouvoir les utiliser. Pour plus d’informations, consultez [Comment : signer à nouveau les manifestes d’application et de déploiement](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Se connecter à l’aide d’un certificat  
 Un certificat est un fichier qui contient une clé unique et l’identité de l’éditeur de solutions. Vous pouvez acheter des certificats à partir d’une autorité de certification, ou créer votre propre certificat et avoir une autorité de certification signez-le.  
  
 Visual Studio connecte avec un certificat temporaire pour activer le débogage des solutions Office. Vous ne devez pas utiliser le certificat temporaire dans des solutions déployées en tant que preuve.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Pour signer une solution Office à l’aide d’un certificat  
  
1.  Sur le **projet** menu, cliquez sur _SolutionName_**propriétés**.  
  
2.  Cliquez sur l’onglet **Signature**.  
  
3.  Sélectionnez **signer les manifestes ClickOnce**.  
  
4.  Recherchez le certificat en cliquant sur **sélectionner dans Store** ou **sélectionner à partir du fichier** et en accédant au certificat.  
  
5.  Pour vérifier que le certificat approprié est utilisé, cliquez sur **plus de détails** pour afficher les informations de certificat.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Accorder votre confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Page Signature, Concepteur de projet](/visualstudio/ide/reference/signing-page-project-designer)  
  
  