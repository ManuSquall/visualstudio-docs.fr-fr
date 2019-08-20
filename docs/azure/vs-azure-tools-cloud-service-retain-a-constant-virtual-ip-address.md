---
title: Conserver une adresse IP virtuelle constante pour un service cloud Azure
description: Découvrez comment vous assurer que l’adresse IP virtuelle de votre service cloud Azure ne change pas.
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ae9064b6aba283c8d2fb8d1e5ec02ef1bd70e199
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260723"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Conserver une adresse IP virtuelle constante pour un service cloud Azure
Lors de la mise à jour d’un service cloud hébergé dans Azure, vérifiez que l’adresse IP virtuelle du service n’est pas modifiée. De nombreux services de gestion de domaine utilisent la méthode DNS (Domain Name System), une méthode d’enregistrement pour stocker des noms de domaine et qui fonctionne uniquement si l’adresse IP virtuelle est inchangée. Utilisez l’**Assistant Publication** dans Azure Tools pour garantir que l’adresse IP virtuelle de votre service cloud ne change pas lors de sa mise à jour. Pour plus d’informations sur l’utilisation de la gestion de domaine DNS pour les services cloud, consultez [Configuration d’un nom de domaine personnalisé pour un service cloud Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publier un service cloud sans modifier son adresse IP virtuelle
L’adresse IP virtuelle d’un service cloud est allouée la première fois que vous la déployez dans Azure dans un environnement spécifique, tel que l’environnement de production. L’adresse IP virtuelle est modifiée uniquement si vous supprimez le déploiement explicitement ou s’il est supprimé implicitement par le processus de mise à jour de déploiement. Pour conserver l’adresse IP virtuelle, vous ne devez pas supprimer votre déploiement, et vous devez vous assurer qu’il n’est pas supprimé automatiquement par Visual Studio.

Vous pouvez spécifier les paramètres de déploiement dans l’**Assistant Publication**, qui prend en charge plusieurs options de déploiement. Vous pouvez spécifier un nouveau déploiement ou une mise à jour de déploiement, qui peut être incrémentielle ou simultanée. Dans ces deux types de mise à jour, l’adresse IP virtuelle est conservée. Pour les définitions de ces différents types de déploiement, consultez [Assistant Publication d’application Azure](vs-azure-tools-publish-azure-application-wizard.md). De plus, vous pouvez contrôler si une erreur se produit, dans le cas de la suppression du déploiement précédent d’un service cloud. L’adresse IP virtuelle peut être modifiée de façon inattendue si cette option n’est pas définie correctement.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Mettre à jour un service cloud sans modifier son adresse IP virtuelle
1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

2. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet. Dans le menu contextuel, sélectionnez **Publier**.

    ![Publish menu](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. Dans la boîte de dialogue **Publication d’application Azure**, sélectionnez l’abonnement Azure vers lequel vous souhaitez effectuer le déploiement. Connectez-vous si nécessaire, puis sélectionnez **Suivant**.

    ![Publication d’application Azure : page de connexion](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Dans l’onglet **Paramètres communs**, vérifiez que le nom du service cloud vers lequel vous souhaitez effectuer le déploiement, **l’environnement**, la **configuration de build** et la **configuration du service** sont corrects.

    ![Publication d’application Azure : onglet Paramètres communs](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Dans l’onglet **Paramètres avancés**, vérifiez que l’**étiquette de déploiement** et le **compte de stockage** sont corrects. Vérifiez que la case **Supprimer le déploiement en cas d’échec** n’est pas cochée et que la case **Mise à jour du déploiement** est cochée. Décocher la case **Supprimer le déploiement en cas d’échec** vous garantit que votre adresse IP virtuelle ne sera pas perdue si une erreur se produit pendant le déploiement. Cocher la case **Mise à jour du déploiement** vous garantit que votre déploiement ne sera pas supprimé et que votre adresse IP virtuelle ne sera pas perdue lorsque vous republierez votre application.

    ![Publication d’application Azure : onglet Paramètres avancés](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Pour préciser davantage comment vous souhaitez mettre à jour les rôles, sélectionnez **Paramètres** en regard de **Mise à jour du déploiement**. Sélectionnez **Mise à jour incrémentielle** ou **Mise à jour simultanée** et sélectionnez **OK**. Choisissez **Mise à jour incrémentielle** pour mettre à jour les instances de votre application l’une après l’autre afin que l’application soit toujours disponible. Choisissez **Mise à jour simultanée** pour mettre à jour toutes les instances de votre application en même temps. La mise à jour simultanée est plus rapide, mais votre service risque de ne pas être disponible pendant la durée du processus de mise à jour. Quand vous avez terminé, cliquez sur **Suivant**.

    ![Publication d’application Azure : page Paramètres du déploiement](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. Dans la boîte de dialogue **Publication d’application Azure**, sélectionnez **Suivant** jusqu’à l’affichage de la page **Résumé**. Vérifiez vos paramètres, puis sélectionnez **Publier**.

    ![Publication d’application Azure : page Résumé](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Étapes suivantes
- [Utilisation de l’Assistant Publication d’application Azure dans Visual Studio](vs-azure-tools-publish-azure-application-wizard.md)
