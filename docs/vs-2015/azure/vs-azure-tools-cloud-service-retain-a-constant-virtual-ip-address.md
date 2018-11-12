---
title: Comment conserver une adresse IP virtuelle constante pour un service cloud Azure | Microsoft Docs
description: Découvrez comment vous assurer que l’adresse IP virtuelle (VIP) de votre service cloud Azure ne change pas.
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001982"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Conserver une adresse IP virtuelle constante pour un service cloud Azure
Lorsque vous mettez à jour un service cloud qui est hébergé dans Azure, vous devrez peut-être vous assurer que l’adresse IP virtuelle (VIP) du service ne change pas. De nombreux services de gestion de domaine utilisent le système DNS (Domain Name) pour l’inscription des noms de domaine. DNS fonctionne uniquement si l’adresse IP virtuelle reste le même. Vous pouvez utiliser la **Assistant Publication** dans Windows Azure Tools pour vous assurer que l’adresse IP virtuelle de votre service cloud ne change pas lorsque vous mettre à jour. Pour plus d’informations sur l’utilisation de gestion de domaine DNS pour les services cloud, consultez [configuration d’un nom de domaine personnalisé pour un service cloud Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publier un service cloud sans modifier son adresse IP virtuelle
L’adresse IP virtuelle d’un service cloud est allouée lorsque vous tout d’abord déployez vers Azure dans un environnement particulier, tel que l’environnement de production. L’adresse IP virtuelle ne change que si vous supprimez le déploiement explicitement ou implicitement la suppression du déploiement par le processus de mise à jour du déploiement. Pour conserver l’adresse IP virtuelle, vous ne devez pas supprimer votre déploiement, et vous devez vous assurer que Visual Studio ne le supprime automatiquement votre déploiement. 

Vous pouvez spécifier des paramètres de déploiement dans le **Assistant Publication**, qui prend en charge plusieurs options de déploiement. Vous pouvez spécifier un nouveau déploiement ou un déploiement de mises à jour, ce qui peut être incrémentielle ou simultanée. Les deux types de déploiement de mise à jour de conservent l’adresse IP virtuelle. Pour les définitions de ces différents types de déploiement, consultez [Assistant Publication d’Application Azure](vs-azure-tools-publish-azure-application-wizard.md). En outre, vous pouvez contrôler si le déploiement précédent d’un service cloud est supprimé si une erreur se produit. Si vous ne définissez pas cette option correctement, l’adresse IP virtuelle peut changer de façon inattendue.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Mettre à jour un service cloud sans modifier son adresse IP virtuelle
1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio. 

2. Dans **l’Explorateur de solutions**, cliquez sur le projet. Dans le menu contextuel, sélectionnez **publier**.

    ![Menu Publier](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. Dans le **publier l’Application Azure** boîte de dialogue, sélectionnez l’abonnement Azure auquel vous souhaitez déployer. Connectez-vous si nécessaire, puis sélectionnez **suivant**.

    ![Publier Azure Application page de connexion](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Sur le **paramètres communs** , vérifiez que le nom du cloud service vers lequel vous effectuez un déploiement, le **environnement**, le **configuration de Build**et le **Configuration du Service** sont corrects.

    ![Publication : onglet Paramètres courants d’Application Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Sur le **paramètres avancés** onglet, vérifiez que le **étiquette du déploiement** et **compte de stockage** sont corrects. Vérifiez que le **supprimer le déploiement en cas d’échec** case à cocher est désactivée et vérifiez que le **mise à jour de déploiement** case à cocher est activée. En désactivant le **supprimer le déploiement en cas d’échec** case à cocher, vous vous assurer que votre adresse IP virtuelle ne sera pas perdue si une erreur se produit pendant le déploiement. En sélectionnant le **mise à jour de déploiement** case à cocher, vous vous assurer que votre déploiement n’est pas supprimé et que votre adresse IP virtuelle ne sera pas perdue lorsque vous republiez votre application. 

    ![Publication : onglet Paramètres avancés de l’Application Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Pour préciser davantage comment vous souhaitez que les rôles à mettre à jour, sélectionnez **paramètres** regard **mise à jour de déploiement**. Sélectionnez **mise à jour incrémentielle** ou **mise à jour simultanée**, puis sélectionnez **OK**. Choisissez **mise à jour incrémentielle** pour mettre à jour chaque instance de votre application, une après l’autre, afin que l’application soit toujours disponible. Choisissez **mise à jour simultanée** pour mettre à jour toutes les instances de votre application en même temps. Mise à jour simultanée est plus rapide, mais votre service ne soient pas disponible pendant le processus de mise à jour. Lorsque vous avez terminé, sélectionnez **suivant**.

    ![Publier la page Paramètres de déploiement d’Application Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. Dans le **publier l’Application Azure** boîte de dialogue, sélectionnez **suivant** jusqu'à ce que le **Résumé** page s’affiche. Vérifiez vos paramètres, puis sélectionnez **publier**.
   
    ![Publier la page Résumé des applications Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Étapes suivantes
- [À l’aide de Visual Studio Assistant Publication d’Azure Application](vs-azure-tools-publish-azure-application-wizard.md)

