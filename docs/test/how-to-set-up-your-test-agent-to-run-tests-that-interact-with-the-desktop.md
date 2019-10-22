---
title: Configurer un agent de test
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55cf32d138d2644e2d2a7a08406eb575a2895400
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653426"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Guide pratique pour configurer votre agent de test afin d’exécuter des tests qui interagissent avec le Bureau

Si vous souhaitez exécuter des tests automatisés qui interagissent avec le bureau, vous devez configurer votre agent pour qu'il s'exécute en tant que processus au lieu de service. Par exemple, si vous voulez exécuter à distance un test codé de l'interface utilisateur à l'aide d'un contrôleur de test et d'un agent de test, ou si vous voulez exécuter un test et capturer un enregistrement vidéo lorsque vous l'exécutez, vous devez configurer votre agent pour qu'il s'exécute en tant que processus. Quand vous attribuez un rôle à des agents dans vos paramètres de test avec Visual Studio ou dans votre environnement avec Microsoft Test Manager, vous devez modifier la configuration de tous les agents affectés à des rôles qui sont amenés à interagir avec le poste de travail.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!WARNING]
> Si vous utilisez Microsoft Test Manager pour configurer un environnement lab, il installe l’agent de test. Vous pouvez spécifier dans **l’Assistant Création de l’environnement** que vous souhaitez configurer l’un des rôles pour exécuter des tests codés de l’interface utilisateur.

> [!IMPORTANT]
> L'ordinateur qui exécute un agent sur lequel vous voulez exécuter des tests codés de l'interface utilisateur ne peut pas être verrouillé ou avoir un écran de veille actif.

Si vous exécutez un test codé de l’interface utilisateur qui lance un navigateur, le compte de service de l’agent de test est utilisé pour lancer ce navigateur. Ce compte de service doit être identique au compte d'utilisateur qui est l'utilisateur actif sur cet ordinateur. S'il ne s'agit pas du même compte d'utilisateur, le navigateur ne démarrera pas.

> [!IMPORTANT]
> Si vous exécutez un test codé de l'interface utilisateur qui lance un navigateur dans le cadre d'une définition de build, le compte de service du service de build est utilisé pour lancer ce navigateur. Ce compte de service doit être identique au compte d'utilisateur qui est l'utilisateur actif sur cet ordinateur. S'il ne s'agit pas du même compte d'utilisateur, le navigateur ne démarrera pas.

Utilisez la procédure suivante pour configurer les agents assignés à un rôle qui effectue une tâche nécessitant une interaction avec le Bureau.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Pour configurer un agent pour qu'il s'exécute en tant que processus

1. Pour configurer l'agent de test que vous avez installé afin qu'il s'exécute en tant que processus, accédez à **Démarrer** > **Outil de configuration de Test Agent**.

   La boîte de dialogue **Configurer Test Agent** s’affiche.

   ![Configurer Visual Studio Test Agent](media/configure-test-agent.png)

2. Sélectionnez **Processus interactif**. L'agent de test sera lancé en tant que processus et non en tant que service. Sélectionnez **Suivant**.

3. Entrez le nom d’utilisateur et le mot de passe de l’utilisateur qui exécutera le processus de l’agent de test.

   > [!NOTE]
   > - L'utilisateur que vous ajoutez pour démarrer le processus doit également être ajouté en tant que membre du groupe TeamTestAgentService sur l'ordinateur du contrôleur de test pour cet agent. Si cet utilisateur est l'utilisateur actuel, vous devez fermer votre session ou redémarrer l'ordinateur lorsque vous l’ajoutez à l'ordinateur de contrôleur de test.
   > - Les mots de passe null ne sont pas pris en charge pour les comptes d'utilisateurs.
   > - Si vous souhaitez utiliser IntelliTrace ou les données d'émulation de réseau et l'adaptateur de diagnostic, le compte d'utilisateur doit être membre du groupe Administrateurs. Si l’ordinateur qui exécute l’agent de test utilise un système d’exploitation avec un compte d’utilisateur de moindre privilège, vous devez également l’exécuter en tant qu’administrateur (avec privilège élevé). Si le nom d'utilisateur de l'agent n'est pas dans le service d'agent, celui-ci essaiera de l'ajouter, ce qui nécessite des autorisations sur le contrôleur de test.
   > - L'utilisateur qui tente d'utiliser le contrôleur de test doit figurer dans le compte Utilisateurs du contrôleur de test. Si ce n'est pas le cas, il ne pourra pas exécuter les tests sur le contrôleur.

4. Pour que l’ordinateur sur lequel est installé un agent de test puisse exécuter des tests après avoir redémarré, vous pouvez configurer l’ordinateur de façon à ce qu’il se connecte automatiquement comme utilisateur de l’agent de test. Sélectionnez **Se connecter automatiquement**. Ainsi, le nom d'utilisateur et le mot de passe seront stockés dans un formulaire chiffré dans le Registre.

   > [!NOTE]
   > Lorsque vous êtes connecté à l'environnement lab à l'aide d'une connexion Bureau à distance ou d'une connexion basée sur invité, des déconnexions fréquentes et inattendues peuvent se produire. Cela peut être dû au fait que l'ordinateur est configuré pour se connecter automatiquement au réseau.

5. Pour vérifier que l’écran de veille est désactivé étant donné que cela peut interférer avec tout test automatisé qui doit interagir avec le poste de travail, sélectionnez **S’assurer que l’écran de veille est désactivé**.

   > [!WARNING]
   > Se connecter automatiquement ou désactiver l'écran de veille présente des risques. En activant la connexion automatique, vous permettez à d'autres utilisateurs de démarrer cet ordinateur et d'utiliser le compte sur lequel il se connecte automatiquement. Si vous désactivez l'écran de veille, l'ordinateur peut ne pas inviter l'utilisateur à ouvrir une session pour déverrouiller l'ordinateur. Cela permet à n'importe quelle personne d'accéder à l'ordinateur dès lors qu'elle peut y accéder physiquement. Si vous activez ces fonctions sur un ordinateur, vous devez vous assurer que ces ordinateurs sont physiquement sécurisés. S'ils se trouvent, par exemple, dans un lab physiquement sécurisé. Si vous désactivez **S’assurer que l’écran de veille est désactivé**, ceci n’active pas votre écran de veille.

   Pour exécuter de nouveau l’agent en tant que service, vous pouvez utiliser cet outil et sélectionner **Service**.

6. Pour appliquer vos modifications, choisissez **Appliquer les paramètres**.

   Une boîte de dialogue **Récapitulatif de la configuration** s’affiche et indique l’état de chacune des étapes pour configurer votre agent de test.

7. Pour fermer la boîte de dialogue **Récapitulatif de la configuration**, choisissez **Fermer**. Ensuite, choisissez à nouveau **Fermer** pour fermer **l’outil de configuration de Test Agent**.

   > [!NOTE]
   > Une icône de zone de notification s'exécute sur l'ordinateur pour un agent de test qui s'exécute en tant que processus. Elle affiche l’état de l’agent de test. Vous pouvez démarrer, arrêter ou redémarrer l'agent s'il s'exécute en tant que processus à l'aide de cet outil. Pour démarrer l’agent de test comme processus s’il n’est pas en cours d’exécution, choisissez **Démarrer** > **Tous les programmes** > **Microsoft Visual Studio Test Agent**.

   Si le contrôleur de test pour cet agent de test est inscrit auprès de Team Foundation Server, l’état d’un agent de test qui s’exécute en tant que processus interactif s’affiche dans la vue **Contrôleurs** dans le **Centre lab** pour Microsoft Test Manager. Il s'affiche précédé d'un astérisque pour indiquer qu'il s'exécute comme un processus interactif. Pour redémarrer cet agent de test, utilisez l’outil qui s’exécute sur l’ordinateur pour l’agent de test, et non la vue **Contrôleurs**.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)