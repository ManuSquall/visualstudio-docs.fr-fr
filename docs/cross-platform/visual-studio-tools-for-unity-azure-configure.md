---
title: "Procédure pas à pas de configuration Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 4e1cf47420cafda2552cdbb625d6d41626c32971
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-easy-tables-in-azure"></a>Configurer les tables faciles dans Azure

Les tables faciles sont une fonctionnalité [d’Azure Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/) qui permettent l’installation et la gestion de tables SQL directement dans l’interface utilisateur graphique du portail Azure. Azure Mobile Apps prend en charge de nombreuses fonctionnalités, mais le cadre de cet exemple se limite à la lecture et l’écriture des données stockées dans un back-end Azure Mobile App à partir d’un projet Unity.

## <a name="create-a-new-azure-mobile-app"></a>Créer une application mobile Azure

Connectez-vous au [portail Azure](https://ms.portal.azure.com). Si vous n’avez pas d’abonnement Azure, la [version d’évaluation gratuite](https://azure.microsoft.com/en-us/free/) ou les crédits inclus de [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) suffisent largement pour effectuer cette procédure pas à pas.

**Une fois dans le portail :**

1. Sélectionnez **Nouveau > Web + Mobile > Application mobile > Créer**.

  ![Créer une application mobile](media/vstu_azure-configure-easy-tables-image1.png)

2. Configurez la nouvelle application mobile :

  * **Nom de l’application**. Cette option permet de générer l’URL utilisée pour se connecter au back-end Azure Mobile App. Vous devez choisir un nom unique, indiqué par la coche verte.

  * **Abonnement**. Choisissez l’abonnement qu’utilise la nouvelle application mobile pour la facturation.

  * **Groupe de ressources**. Les groupes de ressources facilitent la gestion des ressources associées. Par défaut, Azure crée un groupe de ressources portant le même nom que la nouvelle application. Le paramètre par défaut fonctionne bien pour la procédure pas à pas.

  *  **Plan App Service/Emplacement**. Le plan de service dicte la puissance de calcul, l’emplacement et le coût des ressources qu’Azure utilise pour héberger votre nouvelle application mobile. Par défaut, Azure crée un plan de service avec certains paramètres par défaut. Il s’agit de l’option la plus simple pour cette procédure pas à pas. Toutefois, vous pouvez utiliser ce menu pour personnaliser le niveau tarifaire d’un nouveau plan de service ou un emplacement géographique. En outre, les paramètres d’un plan de service peuvent être modifiés après son déploiement.

  ![Créer une application mobile](media/vstu_azure-configure-easy-tables-image2.png)

3. Sélectionnez **Créer** et laissez quelques minutes à Azure pour déployer la nouvelle ressource. Vous voyez une notification dans le portail Azure quand le déploiement est terminé.

## <a name="add-a-new-data-connection"></a>Ajouter une nouvelle connexion de données

4. Une fois le déploiement terminé, cliquez sur le bouton **Toutes les ressources**, puis sélectionnez l’application mobile nouvellement créée.

  ![Sélectionner la nouvelle application mobile](media/vstu_azure-configure-easy-tables-image3.png)

5. Dans le panneau récemment ouvert, faites défiler vers le bas dans le menu du côté gauche et cliquez sur le bouton **Tables faciles**, répertorié sous le titre **MOBILE**.

  ![Sélectionner les tables faciles](media/vstu_azure-configure-easy-tables-image4.png)

6. Cliquez sur la notification de couleur bleue **Vous souhaitez configurer des tables/API faciles ?** qui s’affiche en haut du panneau Tables faciles.

  ![Cliquer sur la notification pour configurer des tables faciles](media/vstu_azure-configure-easy-tables-image5.png)

7. Cliquez sur la notification indiquant **Vous avez besoin d’une base de données pour utiliser les tables faciles. Cliquez ici pour en créer une**.

  ![Cliquer sur la notification pour créer une base de données](media/vstu_azure-configure-easy-tables-image6.png)

8. Dans le panneau Connexions de données, cliquez sur le bouton **Ajouter**.

  ![Cliquer sur le bouton Ajouter](media/vstu_azure-configure-easy-tables-image7.png)

9. Dans le panneau Ajouter la connexion de données, sélectionnez **SQL Database**.

  ![Sélectionner SQL Database](media/vstu_azure-configure-easy-tables-image8.png)

10. Un panneau s’ouvre pour configurer une nouvelle base de données SQL Database et un nouveau serveur SQL Server :

  * **Nom**. Entrez un nom pour la base de données.

  * **Serveur cible**. Cliquez sur **Serveur cible** pour ouvrir le panneau Nouveau serveur.

      * **Nom du serveur**. Entrez un nom pour le serveur.

      * **Connexion d’administrateur du serveur et mot de passe**. Créez un nom d’utilisateur et un mot de passe pour l’administrateur du serveur.

      * **Emplacement**. Choisissez un emplacement proche pour le serveur.

      * Vérifiez que la case **Autoriser les services Azure à accéder au serveur** reste cochée.

      * Cliquez sur **Sélectionner** pour terminer la configuration du serveur.

    * **Niveau tarifaire**. Laissez le paramètre par défaut pour la procédure pas à pas. Ce paramètre peut être modifié ultérieurement.

    * **Classement**. Laissez le paramètre par défaut.

    * Cliquez sur **Sélectionner** pour terminer la configuration de la base de données.

    ![Configurer un serveur SQL Server et une base de données SQL Database](media/vstu_azure-configure-easy-tables-image9.png)

11. De retour dans le panneau Ajouter la connexion de données, cliquez sur **Chaîne de connexion**. Quand le panneau Chaîne de connexion s’affiche, conservez les paramètres par défaut et cliquez sur **OK**.

  ![Cliquer sur Chaîne de connexion](media/vstu_azure-configure-easy-tables-image9.1.png)

12. De retour dans le panneau Ajouter la connexion de données, le texte « MS_TableConnectionString » ne doit plus être en italique. Cliquez sur **OK** et laissez quelques minutes à Azure pour créer la connexion de données. Une notification s’affiche quand le processus est terminé.

  ![Cliquer sur OK](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>Terminer l’initialisation des tables faciles

13. Une fois la connexion de données correctement créée, cliquez sur le bouton **Toutes les ressources**, puis revenez à nouveau vers l’application mobile. Il est important d’effectuer cette étape pour actualiser la notification de configuration des tables faciles.

14. Faites défiler vers le bas et choisissez **Tables faciles**, puis sélectionnez une nouvelle fois la notification de couleur bleue **Vous souhaitez configurer des tables/API faciles ?**.

  ![Cliquer sur la notification des tables faciles](media/vstu_azure-configure-easy-tables-image5.png)

15. Cette fois, le panneau qui s’affiche doit indiquer que « Vous avez déjà une connexion de données » sous le titre **1**. Sous le titre **2**, cliquez sur la case indiquant **Je reconnais que cette opération va remplacer tout le contenu du site.** Cliquez maintenant sur **Initialiser l’application** et attendez quelques minutes qu’Azure termine le processus d’initialisation. Une nouvelle notification indique quand le processus est terminé.

  ![Cliquer sur Initialiser l’application](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>Étape suivante

* [Créer des tables faciles](visual-studio-tools-for-unity-azure-setup.md)
