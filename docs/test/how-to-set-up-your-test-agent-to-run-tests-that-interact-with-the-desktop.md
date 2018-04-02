---
title: Configurer un agent de test Visual Studio pour exécuter des tests qui interagissent avec le poste de travail | Microsoft Docs
ms.date: 10/20/2016
ms.topic: article
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 6953466776872098315cf1b48036bf96d9e570ab
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Comment : configurer votre agent de test pour exécuter des tests qui interagissent avec le bureau

Si vous souhaitez exécuter des tests automatisés qui interagissent avec le bureau, vous devez configurer votre agent pour qu'il s'exécute en tant que processus au lieu de service. Par exemple, si vous voulez exécuter à distance un test codé de l’interface utilisateur à l’aide d’un contrôleur de test et d’un agent de test, ou si vous voulez exécuter un test et capturer un enregistrement vidéo lorsque vous l’exécutez, vous devez configurer votre agent pour qu’il s’exécute en tant que processus. Quand vous affectez des agents à des rôles dans vos paramètres de test avec Visual Studio ou quand vous affectez des agents à des rôles dans votre environnement avec Microsoft Test Manager, vous devez modifier la configuration des agents affectés à des rôles qui doivent interagir avec le poste de travail.

> [!WARNING]
> Si vous utilisez Microsoft Test Manager pour configurer un environnement lab, il installe l’agent de test. Vous pouvez spécifier dans l'assistant de création de l'environnement que vous souhaitez configurer l'un des rôles pour exécuter des tests codés de l'interface utilisateur.

> [!IMPORTANT]
> L'ordinateur qui exécute un agent sur lequel vous voulez exécuter des tests codés de l'interface utilisateur ne peut pas être verrouillé ou avoir un écran de veille actif.

Si vous exécutez un test codé de l'interface utilisateur qui lance un navigateur, le compte de service de l'agent de test est utilisé pour lancer ce navigateur. Ce compte de service doit être identique au compte d'utilisateur qui est l'utilisateur actif sur cet ordinateur. S'il ne s'agit pas du même compte d'utilisateur, le navigateur ne démarrera pas.

> [!IMPORTANT]
> Si vous exécutez un test codé de l'interface utilisateur qui lance un navigateur dans le cadre d'une définition de build, le compte de service du service de build est utilisé pour lancer ce navigateur. Ce compte de service doit être identique au compte d'utilisateur qui est l'utilisateur actif sur cet ordinateur. S'il ne s'agit pas du même compte d'utilisateur, le navigateur ne démarrera pas.

 Utilisez la procédure suivante pour configurer les agents assignés à un rôle qui effectue une tâche nécessitant une interaction avec le Bureau.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Pour configurer un agent pour qu'il s'exécute en tant que processus

1.  Pour configurer l’agent de test installé pour qu’il s’exécute en tant que processus, accédez à **Démarrer**, **Tous les programmes**, **Microsoft Visual Studio**, **Outil de configuration de Microsoft Visual Studio Test Agent**.

     La boîte de dialogue **Configurer l’agent de test** s’affiche.

2.  Pour voir la page permettant de choisir d’exécuter en tant que processus, choisissez **Options d’exécution**.

     La page qui s'affiche vous permet de sélectionner une exécution de l'agent en tant que processus ou service.

3.  Sélectionnez **Processus interactif**. L’agent de test sera lancé en tant que processus et non en tant que service. Sélectionnez **Suivant**.

     Vous pouvez maintenant entrer les détails de l’utilisateur à utiliser lorsque vous exécutez l’agent de test en tant que processus ou autre.

    > [!NOTE]
    > L’utilisateur que vous ajoutez pour démarrer le processus doit également être ajouté en tant que membre du groupe TeamTestAgentService sur l’ordinateur du contrôleur de test pour cet agent. Si cet utilisateur est l'utilisateur actuel, lorsque vous ajoutez cet utilisateur à l'ordinateur de contrôleur de test, vous devez fermer votre session ou redémarrer l'ordinateur.

4.  Tapez le nom dans **Nom d’utilisateur**.

5.  Tapez le mot de passe dans **Mot de passe**.

     **Informations importantes sur le compte d’utilisateur**

    -   Les mots de passe null ne sont pas pris en charge pour les comptes d'utilisateurs.

    -   Si vous souhaitez utiliser IntelliTrace ou les données d'émulation de réseau et l'adaptateur de diagnostic, le compte d'utilisateur doit être membre du groupe Administrateurs. Si l’ordinateur qui exécute l’agent de test utilise un système d’exploitation avec un compte d’utilisateur de moindre privilège, vous devez également l’exécuter en tant qu’administrateur (avec privilège élevé). Si le nom d'utilisateur de l'agent n'est pas dans le service d'agent, celui-ci essaiera de l'ajouter, ce qui nécessite des autorisations sur le contrôleur de test.

    -   L'utilisateur qui essaie d'utiliser le contrôleur de test doit figurer dans le compte Utilisateurs du contrôleur de test. Si ce n'est pas le cas, il ne pourra pas exécuter les tests sur le contrôleur.

6.  Pour vous assurer qu’un ordinateur sur lequel est installé un agent de test puisse exécuter des tests après avoir redémarré, vous pouvez configurer l’ordinateur pour qu’il se connecte automatiquement en tant que l’utilisateur de l’agent de test. Sélectionnez **Se connecter automatiquement**. Ainsi, le nom d'utilisateur et le mot de passe seront stockés dans un formulaire chiffré dans le Registre.

    > [!NOTE]
    > Lorsque vous êtes connecté à l'environnement lab à l'aide d'une connexion Bureau à distance ou d'une connexion basée sur invité, des déconnexions fréquentes et inattendues peuvent se produire. Cela peut être dû au fait que l'ordinateur est configuré pour se connecter automatiquement au réseau.

7.  Pour garantir que l’écran de veille est désactivé, car cela peut interférer avec les tests automatisés qui doivent interagir avec le poste de travail, sélectionnez **S’assurer que l’écran de veille est désactivé**.

    > [!WARNING]
    > Se connecter automatiquement ou désactiver l'écran de veille présente des risques. En activant la connexion automatique, vous permettez à d'autres utilisateurs de démarrer cet ordinateur et d'utiliser le compte sur lequel il se connecte automatiquement. Si vous désactivez l'écran de veille, l'ordinateur peut ne pas inviter l'utilisateur à ouvrir une session pour déverrouiller l'ordinateur. Cela permet à n'importe quelle personne d'accéder à l'ordinateur dès lors qu'elle peut y accéder physiquement. Si vous activez ces fonctionnalités sur un ordinateur, vous devez vous assurer que ces ordinateurs sont physiquement sécurisés. S'ils se trouvent, par exemple, dans un lab physiquement sécurisé. Si vous désactivez **S’assurer que l’écran de veille est désactivé**, ceci n’active pas votre écran de veille.

     Pour exécuter de nouveau l’agent en tant que service, vous pouvez utiliser cet outil et sélectionner **Service**.

8.  Pour appliquer vos modifications, choisissez **Appliquer les paramètres**.

     Une boîte de dialogue **Récapitulatif de la configuration** s’affiche et indique l’état de chacune des étapes pour configurer votre agent de test.

9. Pour fermer la boîte de dialogue **Récapitulatif de la configuration**, choisissez **Fermer**. Choisissez ensuite à nouveau **Fermer** pour fermer l’outil de configuration de Test Agent.

    > [!NOTE]
    > Une icône de zone de notification s’exécute sur l’ordinateur pour un agent de test qui s’exécute en tant que processus. Elle affiche l'état de l'agent de test. Vous pouvez démarrer, arrêter ou redémarrer l'agent s'il s'exécute en tant que processus à l'aide de cet outil. Pour démarrer l’agent de test en tant que processus s’il n’est pas en cours d’exécution, choisissez **Démarrer**, **Tous les programmes**, **Microsoft Visual Studio**, **Microsoft Visual Studio Test Agent**.

     Si le contrôleur de test pour cet agent de test est inscrit auprès de Team Foundation Server, l’état d’un agent de test qui s’exécute en tant que processus interactif s’affiche dans la vue **Contrôleurs** dans le **Centre lab** pour Microsoft Test Manager. Il s'affiche précédé d'un astérisque pour indiquer qu'il s'exécute comme un processus interactif. Pour redémarrer cet agent de test, vous devez utiliser l’outil s’exécute sur l’ordinateur pour l’agent de test et non pas la vue **Contrôleurs**.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)