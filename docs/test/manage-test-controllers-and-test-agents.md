---
title: Gérer les contrôleurs de test et les agents de test dans Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d99d01dbe26354b8a3b3afa18d1337c64d1b390
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="manage-test-controllers-and-test-agents"></a>Gérer les contrôleurs de test et les agents de test

Si vous voulez utiliser Visual Studio pour exécuter des tests à distance, distribuer des tests sur plusieurs ordinateurs ou exécuter des tests de charge, vous devez configurer un contrôleur de test, des agents de test et un fichier de paramètres de test. Cette rubrique explique comment gérer des contrôleurs de test et des agents de test après les avoir installés et configurés pour la première fois.

Si vous utilisez Microsoft Test Manager pour exécuter des tests dans des environnements lab, vous gérez les contrôleurs de test et leurs agents en utilisant le **Gestionnaire de contrôleurs de test** dans le **Centre lab** pour Microsoft Test Manager. Cette rubrique s'applique seulement si vous utilisez Visual Studio pour exécuter vos tests.

Pour plus d’informations sur l’installation et la configuration des agents et des contrôleurs de test pour exécuter des tests dans Visual Studio, consultez [Configurer des agents et des contrôleurs de test](../test/configure-test-agents-and-controllers-for-load-tests.md).

Pour permettre la configuration et la surveillance du contrôleur de test et des agents inscrits, le projet de test qui contient les tests à exécuter doit comprendre un fichier de paramètres de test. Ouvrez le fichier de paramètres de test, choisissez **Rôle**, puis **Gérer les contrôleurs de test** dans la liste déroulante du champ **Contrôleur**.

Pour les projets de tests de charge, vous pouvez également choisir **Gérer les contrôleurs de test** dans le menu **Test de charge**.

## <a name="add-a-test-agent-to-a-test-controller"></a>Ajouter un agent de test à un contrôleur de test

Il est possible d’ajouter un agent de test à un contrôleur de test différent et d’ajouter un agent de test à un contrôleur de test que vous venez d’installer.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Pour ajouter un agent de test à un contrôleur de test

1. Choisissez **Démarrer** > **Outil de configuration de Test Agent**.

     La boîte de dialogue **Configurer Test Agent** s’affiche.

    > [!NOTE]
    > Un agent de test doit déjà être installé pour pouvoir l’ajouter à un contrôleur de test. Pour plus d’informations sur la façon d’installer un agent de test, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

2. Si vous souhaitez modifier le mode d’exécution de l’agent de test, choisissez **Options d’exécution**.

     Deux options s’affichent pour vous permettre de définir le mode d’exécution de l’agent de test :

     **Service** Si vous n’avez pas à exécuter de tests automatisés qui interagissent avec le poste de travail (tests codés de l’interface utilisateur, par exemple) ni à créer un enregistrement vidéo lors de l’exécution de votre test, sous **Exécuter l’agent de test en tant que**, sélectionnez **Service**. L’agent de test démarrera en tant que service. Sélectionnez **Suivant**.

     Vous pouvez maintenant entrer les détails relatifs à l’utilisateur lorsque l’agent de test démarre en tant que service.

    1. Entrez le nom dans **Nom d’utilisateur**.

    2. Entrez le mot de passe dans **Mot de passe**.

        |**Informations importantes sur le compte d’utilisateur**|
        |--------------------------------------------|
        |- Les mots de passe null ne sont pas pris en charge pour les comptes d’utilisateurs.|
        |- Si vous souhaitez utiliser le collecteur IntelliTrace ou l’émulation réseau, le compte d’utilisateur doit être membre du groupe Administrateurs.|
        |- Si le nom d’utilisateur de l’agent n’est pas dans le service d’agent, celui-ci essaiera de l’ajouter, ce qui nécessite des autorisations sur le contrôleur de test.|
        |- L’utilisateur qui essaie d’utiliser le contrôleur de test doit figurer dans le compte Utilisateurs du contrôleur de test ; sinon il ne pourra pas exécuter les tests sur le contrôleur.|

     **Processus interactif** Si vous souhaitez exécuter des tests automatisés qui doivent interagir avec le poste de travail (tests codés de l’interface utilisateur, par exemple) ou créer un enregistrement vidéo lors de l’exécution de votre test, sélectionnez **Processus interactif**. L’agent de test démarrera en tant que processus interactif et non en tant que service.

     Sur la page suivante, entrer les détails relatifs à l’utilisateur lorsque l’agent de test démarre en tant que processus, ainsi que d’autres options.

    1. Entrez le nom dans **Nom d’utilisateur**.

    2. Entrez le mot de passe dans **Mot de passe**.

        > [!NOTE]
        > Si vous configurez l’agent de test pour qu’il fonctionne en tant que processus interactif avec un autre utilisateur qui n’est pas l’utilisateur actuellement actif, vous devez redémarrer l’ordinateur et ouvrir une session avec cet autre utilisateur pour pouvoir démarrer l’agent. Les mots de passe null ne sont par ailleurs pas pris en charge pour les comptes d'utilisateurs. Si vous souhaitez utiliser le collecteur IntelliTrace ou l'émulation de réseau, le compte d'utilisateur doit être membre du groupe Administrateurs.

        |**Informations importantes sur le compte d’utilisateur**|
        |--------------------------------------------|
        |- Les mots de passe null ne sont pas pris en charge pour les comptes d’utilisateurs.|
        |- Si vous souhaitez utiliser IntelliTrace ou les données d’émulation réseau et l’adaptateur de diagnostic, le compte d’utilisateur doit être membre du groupe Administrateurs. Si l’ordinateur qui exécute l’agent de test utilise un système d’exploitation avec un compte d’utilisateur de moindre privilège, vous devez également l’exécuter en tant qu’administrateur (avec privilège élevé).|
        |- Si le nom d’utilisateur de l’agent n’est pas dans le service d’agent, celui-ci essaiera de l’ajouter, ce qui nécessite des autorisations sur le contrôleur de test.|
        |- L’utilisateur qui essaie d’utiliser le contrôleur de test doit figurer dans le compte Utilisateurs du contrôleur de test ; sinon il ne pourra pas exécuter les tests sur le contrôleur.|

    3. Pour vérifier qu’un ordinateur sur lequel est installé un agent de test puisse exécuter des tests après avoir redémarré, vous pouvez configurer l’ordinateur de sorte qu’il ouvre automatiquement une session avec l’utilisateur de l’agent de test. Sélectionnez **Se connecter automatiquement**. Ainsi, le nom d'utilisateur et le mot de passe seront stockés dans un formulaire chiffré dans le Registre.

    4. Pour vérifier que l’écran de veille est désactivé étant donné que cela peut interférer avec tout test automatisé qui doit interagir avec le poste de travail, sélectionnez **S’assurer que l’écran de veille est désactivé**.

        > [!WARNING]
        > Se connecter automatiquement ou désactiver l'écran de veille présente des risques. En activant la connexion automatique, vous permettez à d'autres utilisateurs de démarrer cet ordinateur et d'utiliser le compte sur lequel il se connecte automatiquement. Si vous désactivez l'écran de veille, l'ordinateur peut ne pas inviter l'utilisateur à ouvrir une session pour déverrouiller l'ordinateur. Tout personne peut ainsi accéder à l'ordinateur, à partir du moment où celle-ci peut y accéder physiquement. Si vous activez ces fonctionnalités sur un ordinateur, vous devez vous assurer que ces ordinateurs sont physiquement sécurisés. S'ils se trouvent, par exemple, dans un lab physiquement sécurisé. (La désactivation de l’option **S’assurer que l’écran de veille est désactivé** ne permet pas d’activer l’écran de veille.)

3. Pour inscrire cet agent auprès d’un contrôleur de test différent, sélectionnez **Inscrire auprès du contrôleur de test**. Tapez le nom de votre contrôleur de test suivi de **:** et le numéro de port que vous utilisez dans **Inscrire l’agent de test auprès du contrôleur de test suivant**. Par exemple, tapez **agent1:6901**.

    > [!NOTE]
    > Le numéro de port par défaut est 6901.

4. Pour enregistrer vos changements, choisissez **Appliquer les paramètres**. Fermez la boîte de dialogue **Résumé de la configuration**, puis quittez l’outil de configuration de Test Agent.

> [!WARNING]
> Si l’agent est actuellement configuré pour s’exécuter sur un autre contrôleur de test, vous devez supprimer l’agent de test de ce contrôleur.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Supprimer un agent de test d’un contrôleur de test

Pour pouvoir être supprimé, un agent de test doit être hors connexion.

> [!NOTE]
> Vous ne pouvez pas utiliser cette procédure pour supprimer les agents inscrits auprès d'un contrôleur dans le cadre d'un environnement lab. Pour supprimer ces agents d'un contrôleur, vous devez supprimer l'environnement à l'aide de Microsoft Test Manager.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Pour supprimer un agent de test d'un contrôleur de test

1. Si le contrôleur de test n’est pas inscrit auprès d’un projet d’équipe, suivez les étapes suivantes.

    1. Dans Visual Studio, ouvrez le fichier de paramètres de test de votre projet de test, choisissez **Rôle**, puis **Gérer les contrôleurs de test** dans la liste déroulante du champ **Contrôleur**.

         La boîte de dialogue **Administrer le contrôleur de test** s’affiche.

    2. Dans la liste déroulante **Contrôleur**, tapez le nom de l’ordinateur sur lequel vous avez installé le contrôleur de test. Si vous avez précédemment administré un contrôleur de test spécifique, vous pouvez sélectionner son nom dans la liste.

    3. Dans le volet **Agents**, sélectionnez le nom de l’agent de test. Si l’agent est encore en ligne, choisissez **Hors connexion**. Pour le supprimer, choisissez **Supprimer**.

        > [!NOTE]
        > La suppression d’un agent de test ne fait que le dissocier du contrôleur de test. Pour désinstaller complètement l’agent de test, utilisez **Programmes et fonctionnalités** dans le Panneau de configuration sur l’ordinateur de l’agent de test.

2. Si le contrôleur de test est inscrit auprès d’un projet d’équipe, supprimez l’agent à l’aide de Microsoft Test Manager.

## <a name="change-the-settings-for-a-test-agent"></a>Changer les paramètres d’un agent de test

Les statuts possibles d’un agent de test sont les suivants :

|Status|Description|
|------------|-----------------|
|Exécution du test en cours|L'exécution des tests est en cours.|
|Prêt|Disponible pour l'exécution de tests et la collecte de données et de diagnostics|
|Hors connexion|Non disponible pour l'exécution de tests et la collecte de données et de diagnostics|
|Déconnecté|L’agent de test n’est pas lancé|

Vous pouvez modifier l'état et d'autres paramètres pour les agents de test à l'aide des procédures suivantes.

### <a name="to-change-the-settings-of-a-test-agent"></a>Pour modifier les paramètres d’un agent de test

> [!NOTE]
> Si l’agent de test est inscrit auprès d’un contrôleur de test inscrit auprès d’un projet d’équipe, changez les paramètres dans Microsoft Test Manager.

1. Pour configurer et monitorer le contrôleur de test et les agents inscrits pour un test de charge, choisissez le menu **Test de charge** dans Visual Studio, puis choisissez **Gérer les contrôleurs de test**. Pour tout autre type de test, ouvrez le fichier de paramètres de test de votre projet de test dans Visual Studio, choisissez **Rôle**, puis **Gérer les contrôleurs de test** dans la liste déroulante du champ **Contrôleur**.

   La boîte de dialogue **Gérer le contrôleur de test** s’ouvre.

1. Sélectionnez le nom du contrôleur de test dont vous voulez modifier les agents de test dans la liste des contrôleurs de test. Si le contrôleur de test n'apparaît pas dans la liste, vérifiez que le contrôleur de test est inscrit correctement. Pour plus d'informations, lisez la procédure suivante concernant la configuration d'un contrôleur de test.

1. (Facultatif) Dans le volet **Agents de test**, sélectionnez l’ordinateur de l’agent de test dont vous voulez changer les propriétés.

1. Choisissez **Propriétés**.

1. Modifiez les propriétés de l’agent de test suivantes si nécessaire :

|Propriété de l’agent de test|Description|
|-------------------------|-----------------|
|**Poids**|Utilisé pour distribuer la charge lorsque vous utilisez des agents de test avec des niveaux de performance différents. Par exemple, un agent de test avec un poids de 100 reçoit une charge deux fois supérieure à celle d’un agent de test avec un poids de 50.|
|**Commutation IP**|Utilisé pour configurer la commutation IP. La commutation IP permet à un agent de test d'envoyer des demandes à un serveur à l'aide d'une plage d'adresses IP. Cela simule des appels provenant de différents ordinateurs clients.<br /><br /> La commutation IP est importante si votre test de charge accède à une batterie de serveurs web. La plupart des programmes d'équilibrage de charge établissent l'affinité entre un client et un serveur web particulier en utilisant l'adresse IP du client. Si toutes les demandes semblent provenir d'un seul client, l'équilibrage de charge n'équilibre pas la charge. Pour obtenir le bon équilibre de charge dans la batterie de serveurs web, assurez-vous que les demandes proviennent d’une plage d’adresses IP. **Remarque :** Vous pouvez spécifier une carte réseau ou utiliser **(Non assigné)** pour sélectionner automatiquement une carte réseau qui n’est pas actuellement utilisée. <br /><br /> Pour utiliser la fonctionnalité de commutation IP, le service Visual Studio Test Agent doit s’exécuter en tant qu’utilisateur du groupe Administrateurs de cet ordinateur agent. Cet utilisateur est sélectionné pendant la configuration de l'agent, mais peut être modifié en modifiant les propriétés du service puis en le redémarrant.<br /><br /> Pour vérifier que la commutation IP fonctionne correctement, activez le processus d’enregistrement du journal d’IIS sur le serveur web, puis utilisez les fonctionnalités de ce processus pour vérifier que les requêtes proviennent des adresses IP que vous avez configurées.|
|**Attributs**|Ensemble de paires nom/valeur qui peuvent être utilisées dans la sélection d’agent de test. Par exemple, un test peut exiger un système d'exploitation particulier. Vous pouvez ajouter des attributs dans l’onglet **Rôles** de votre fichier de paramètres de test et ils peuvent être utilisés pour sélectionner un agent de test qui a des attributs identiques. Si vous voulez exécuter un test sur plusieurs ordinateurs, créez un attribut dans le rôle de paramètres de test qui est configuré pour exécuter vos tests, puis configurez un attribut correspondant sur chaque agent de test que vous utilisez dans ce rôle. **Remarque :** Ce paramètre est uniquement disponible pour les agents de test inscrits auprès d’un contrôleur de test qui n’est lui-même pas inscrit auprès d’un projet d’équipe, car ces attributs sont utilisés uniquement dans les paramètres de test pour Visual Studio.|

Les modifications du poids et des attributs des agents de test sont appliquées immédiatement, mais n’affectent pas les tests en cours d’exécution. La plage d'adresses IP prend effet après le redémarrage du contrôleur de test.

(Facultatif) Pour modifier l'état d'un agent de test, sélectionnez l'agent dans la liste puis sélectionnez une action parmi les choix disponibles, en fonction de l'état actuel de l'agent.

> [!NOTE]
> Si votre agent de test s'exécute en tant que processus, il est possible de gérer l'état de l'agent de test à partir de l'icône de zone de notification qui s'exécute sur l'ordinateur sur lequel est installé votre agent de test. Elle indique l'état de l'agent de test. Vous pouvez démarrer, arrêter ou redémarrer l'agent s'il s'exécute en tant que processus à l'aide de cet outil. Pour démarrer l’agent de test comme processus s’il ne s’exécute pas, choisissez **Démarrer**, **Tous les programmes**, **Microsoft Visual Studio**, **Microsoft Visual Studio Test Agent**. Cela ajoute l'icône de zone de notification.

## <a name="configure-a-test-controller"></a>Configurer un contrôleur de test

Pour configurer un contrôleur de test, vous devez utiliser **l’outil de configuration du Contrôleur Team Test**. Lorsque vous configurez votre contrôleur de test, vous pouvez l’inscrire auprès d’une autre collection de projets d’équipe ou annuler son inscription auprès d’une collection de projets d’équipe.

Si vous souhaitez inscrire votre contrôleur de test auprès de votre collection de projets Team Foundation Server, le compte que vous utilisez pour le service de contrôleur de test doit être membre du groupe Project Collection Test Service Accounts pour la collection de projets d’équipe, ou le compte que vous utilisez pour exécuter l’outil de configuration du contrôleur de test doit être administrateur de collections de projets.

> [!NOTE]
> Si vous annulez l’inscription d’un contrôleur de test auprès d’une collection de projets d’équipe pour laquelle des environnements sont définis, les environnements sont conservés si vous déplacez cette collection de projets d’équipe et réinscrivez le contrôleur de test auprès de cette dernière.

### <a name="to-configure-a-test-controller"></a>Pour configurer un contrôleur de test

1. Pour exécuter l’outil afin de reconfigurer votre contrôleur de test à tout moment, choisissez **Démarrer** > **Tous les programmes** >  **Microsoft Visual Studio** > **Outil de configuration de Microsoft Visual Studio Test Controller**.

     La boîte de dialogue **Configurer le contrôleur de test** s’affiche.

2. Sélectionnez l'utilisateur à utiliser comme compte d'ouverture de session pour votre service de contrôleur de test.

    > [!NOTE]
    > Les mots de passe null ne sont pas pris en charge pour les comptes d'utilisateurs.

4. (Facultatif) Si vous ne voulez pas utiliser votre contrôleur de test dans un environnement lab, mais uniquement pour exécuter des tests à partir de Visual Studio, désactivez **Inscrire auprès de la collection de projets d’équipe**.

5. (Facultatif) Pour configurer votre contrôleur de test pour le test de charge, sélectionnez **Configurer pour le test de charge**. Tapez ensuite votre instance SQL Server dans **Créer une base de données de résultats de test de charge dans l’instance SQL Server suivante**.

> [!NOTE]
> Pour plus d’informations sur la résolution des problèmes liés aux contrôleurs de test, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Gérer des agents durant l’exécution de vos tests avec un contrôleur de test

Quand vous ajoutez des rôles à vos paramètres de test pour Visual Studio, vous pouvez également ajouter des propriétés d'agent pour chacun des rôles. Ceci détermine quels agents de test sont disponibles pour ce rôle. Lorsque vous exécutez vos tests en utilisant ces paramètres de test, le contrôleur de test sélectionné détermine la disponibilité des agents obligatoires. Les scénarios possibles sont alors les suivants :

-   Aucun agent n'est disponible pour le rôle qui doit exécuter les tests. Vos tests ne peuvent pas être exécutés. Vous pouvez exécuter l'une des actions suivantes puis exécuter vos tests de nouveau :

    -   Vous pouvez attendre qu'un agent devienne disponible pour ce rôle pour exécuter les tests.

    -   Si certains agents hors connexion peuvent être utilisés pour ce rôle, vous pouvez redémarrer l'agent afin qu'il devienne disponible.

    -   Vous pouvez ajouter un autre agent, avec les propriétés d'agent appropriées pour ce rôle, au contrôleur de test.

    -   Vous pouvez modifier les propriétés d'agent pour ce rôle dans les paramètres de test pour activer les autres agents que vous voulez utiliser.

-   Aucun agent n'est disponible pour un ou plusieurs rôles qui exécutent les adaptateurs de données de diagnostic. Vos tests peuvent être exécutés, mais l'adaptateur de données de diagnostic ne peut pas être exécuté. Vous pouvez exécuter vos tests sans l'adaptateur de données de diagnostic ou vous pouvez exécuter l'une des actions suivantes et exécuter vos tests de nouveau :

    -   Vous pouvez attendre qu'un agent devienne disponible pour ces rôles.

    -   Si des agents hors connexion peuvent être utilisés pour ce rôle, vous devez les mettre en ligne à partir de **Administrer le contrôleur de test** dans le menu **Test**. De plus, vous devrez peut-être redémarrer l'agent s'il a été déconnecté du contrôleur.

    -   Vérifiez que tous les agents dont vous pouvez avoir besoin pour cette série de tests ne sont pas en cours d'exécution. Vous pouvez vérifier l’état des agents à partir de **Administrer le contrôleur de test** dans le menu **Test**.

    -   Vous pouvez ajouter un autre agent, avec les propriétés d'agent appropriées pour ce rôle, au contrôleur de test.

    -   Vous pouvez modifier les propriétés d'agent pour ce rôle dans les paramètres de test pour activer les autres agents que vous voulez utiliser.

## <a name="load-tests-from-delay-signed-assemblies"></a>Charger des tests à partir d’assemblys de tests à signature différée

Le contrôleur de test et les agents de test ne peuvent charger que les assemblys de tests fortement signés ou non signés. Certains assemblys de tests sont à signature différée, car ils doivent avoir accès à des assemblys de production pour l'application. Toutefois, ces assemblys ne sont pas fortement signés, car il s'agit uniquement d'assemblys de tests qui ne sont pas distribués. Ces assemblys ne peuvent pas être chargés, car il s'agit d'assemblys à signature différée ; par conséquent, vous devez désactiver la vérification de nom fort pour ces assemblys sur tous les ordinateurs où ils sont chargés, y compris sur l'ordinateur du contrôleur de test. Pour désactiver la vérification à signature différée, utilisez sn.exe. Le jeton de clé publique de l'assembly à signature différée pour lequel la vérification de nom fort doit être ignorée peut être également à inclure.

Utilisez l’outil Sn.exe (Strong Name) pour désactiver la vérification de signature différée.

Cela désactive la vérification des noms forts, pour l'assembly spécifié uniquement, sur l'ordinateur sur lequel vous exécutez la commande. Vous ne pouvez le faire que si vous disposez des autorisations suffisantes.

À l'issue de la série de tests, réactivez la vérification de signature différée via la commande SN.exe.

L'utilisation des commandes SN.exe dans les scripts est recommandée pour désactiver et réactiver la vérification de signature. Vous pouvez désactiver la vérification dans un script d'installation et la réactiver dans un script de nettoyage.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)