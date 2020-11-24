---
title: Créer un paramètre de test pour un test de charge distribué
description: Découvrez comment configurer des paramètres de test pour vos tests de charge afin de pouvoir distribuer ces tests sur plusieurs ordinateurs à l’aide d’agents de test et de contrôleurs de test.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b52fad24cf0772099e619b08ad877bae891365c3
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439964"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Comment : créer un fichier de paramètres de test pour un test de charge distribué

Configurez des *paramètres de test* pour vos tests de charge afin de pouvoir distribuer ces tests sur plusieurs ordinateurs en utilisant des agents de test et des contrôleurs de test. Vous pouvez aussi configurer des paramètres de test pour utiliser des *adaptateurs de données de diagnostic*, qui spécifient les types de données que vous voulez collecter ou la façon d’affecter les ordinateurs de test quand vous exécutez des tests de charge depuis Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Par exemple, vous pouvez utiliser l'adaptateur de données de diagnostic du profileur ASP.NET pour collecter la répartition des performances du code. En outre, les adaptateurs de données de diagnostic peuvent être utilisés pour simuler des goulots d'étranglement potentiels sur l'ordinateur de test ou pour réduire la mémoire système disponible.

Les paramètres de test de Visual Studio sont stockés dans un fichier. Les paramètres de test définissent les informations suivantes sur chaque rôle :

- l'ensemble des rôles qui sont requis pour l'application testée ;

- le rôle à utiliser pour exécuter vos tests ;

- les adaptateurs de données de diagnostic à utiliser pour chaque rôle.

Lorsque vous exécutez vos tests, vous sélectionnez les paramètres de test à utiliser comme paramètres de test actifs en fonction de vos besoins pour cette série de tests. Le fichier de paramètres de test est stocké dans votre solution. L’extension du nom de fichier est *.testsettings*.

Quand vous ajoutez un projet de test de performances de site Web et de charge à une solution, un fichier *. testsettings par défaut* est créé. Le fichier est ajouté automatiquement à la solution dans le dossier **Éléments de solution**. Ce fichier exécute localement vos tests sans adaptateur de données de diagnostic. Vous pouvez ajouter un autre fichier *.testsettings* ou modifier un fichier *.testsettings* pour spécifier les adaptateurs de données de diagnostic et les contrôleurs de test.

Le contrôleur de test aura des agents pouvant être utilisés pour chaque rôle dans vos paramètres de test. Pour plus d’informations sur les contrôleurs de test et les agents de test, consultez [Gérer les contrôleurs de test et les agents de test avec Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Utilisez les étapes suivantes pour créer et supprimer des paramètres de test dans votre solution pour les tests de charge que vous prévoyez d'exécuter depuis Visual Studio.

## <a name="create-a-test-settings-file"></a>Créer un fichier de paramètres de test

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **éléments de solution**, pointez sur **Ajouter**, puis choisissez **nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.

2. Dans le volet **Modèles installés**, choisissez **Paramètres de test**.

3. (Facultatif) Dans la zone **Nom**, changez le nom du fichier de paramètres de test.

4. Choisissez **Ajouter**.

     Le nouveau fichier de paramètres de test s’affiche dans **Explorateur de solutions**, sous le dossier **éléments de solution** .

5. La boîte de dialogue **Paramètres de test** s’affiche. La page **Général** est sélectionnée.

     Vous pouvez maintenant modifier et enregistrer des valeurs de paramètres de test.

6. Sous **Nom**, tapez le nom des paramètres de test.

7. (Facultatif) Sous **Description**, tapez une description pour le paramètre de test afin que les autres membres de l’équipe sachent à quoi il est destiné.

8. (Facultatif) Pour sélectionner le schéma de nommage par défaut pour vos séries de tests, sélectionnez **Schéma d’affectation de nom par défaut**. Pour définir votre propre schéma de nommage, sélectionnez **Schéma défini par l’utilisateur**, puis tapez le texte que vous voulez dans **Texte du préfixe**. Pour ajouter l’horodatage au nom de la série de tests, sélectionnez **Ajouter un horodatage**.

9. Cliquez sur **Rôles**.

     La page **Rôles** s’affiche.

     ![Rôle de paramètres de test](../test/media/load_testtestrole.png)

10. Pour exécuter vos tests à distance, ou pour exécuter vos tests à distance et collecter des données à distance, utilisez la liste déroulante **Méthode d’exécution des tests** et sélectionnez **Exécution distante**.

11. Utilisez la liste déroulante Contrôleur pour sélectionner un contrôleur de test pour les agents de test, qui sera utilisé pour exécuter vos tests ou pour collecter des données.

    > [!NOTE]
    > Si vous ajoutez un contrôleur pour la première fois, aucun contrôleur n'est répertorié dans la liste déroulante. La liste est remplie par les contrôleurs précédents que vous avez définis dans d'autres paramètres de test. Vous devez taper le nom du contrôleur dans la zone (par exemple **TestControllerMachine1**).

12. Pour ajouter les rôles que vous souhaitez utiliser pour exécuter des tests et collecter des données, sous **Rôles**, choisissez **Ajouter**.

13. Dans la colonne **Nom**, tapez un nom pour le rôle. Le rôle peut être, par exemple, "Serveur Web".

14. Répétez les étapes 12 et 13 pour ajouter tous les rôles dont vous avez besoin.

     Chaque rôle utilise un agent de test géré par le contrôleur de test.

15. Sélectionnez le rôle que vous souhaitez pour exécuter vos tests, puis choisissez **Définir en tant que rôle pour exécuter les tests**.

    > [!IMPORTANT]
    > Les autres rôles que vous créez et que vous définissez n’exécutent pas de tests. Ils sont utilisés seulement pour collecter des données en fonction des adaptateurs de données et de diagnostic que vous spécifiez pour les rôles dans la page **Données et diagnostic**.

16. Pour limiter les agents pouvant être utilisés pour un rôle, sélectionnez le rôle, puis choisissez **Ajouter** dans la barre d’outils sous **attributs de l’agent pour le rôle sélectionné**.

     La boîte de dialogue **Règle de sélection d’agent** s’affiche.

     Tapez le nom dans **Nom de l’attribut** et la valeur dans **Valeur d’attribut**, puis choisissez **OK**. Ajoutez autant d'attributs que nécessaire.

     Par exemple, vous pouvez ajouter un attribut nommé « RAM > 16 Go » dont la valeur est « True » ou « False » pour filtrer les ordinateurs d’agents de test dont la capacité de mémoire est supérieure à 16 Go. Pour appliquer un même attribut à un ou plusieurs agents de test, vous utilisez la boîte de dialogue **Gérer les contrôleurs de test**. Pour plus d’informations, consultez [Gérer les contrôleurs de test et des agents de test avec Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Choisissez **Données et diagnostics**.

     La page **Données et diagnostics** s’affiche.

     ![Données de paramètres de test et diagnostics](../test/media/load_testtest.png)

18. Dans la page **Données et diagnostics**, vous définissez le rôle en sélectionnant les *adaptateurs de données de diagnostic* que le rôle utilisera pour collecter des données. Ainsi, si un ou plusieurs adaptateurs de données de diagnostic sont activés pour le rôle, le contrôleur de test choisira un ordinateur agent de test disponible pour collecter des données pour les adaptateurs de données de diagnostic spécifiés, selon les attributs définis pour le rôle. Pour sélectionner les données et les adaptateurs de données de diagnostic que vous voulez collecter pour chaque rôle, choisissez le rôle. Pour chaque rôle, sélectionnez les adaptateurs de données de diagnostic en fonction des besoins liés aux tests. Pour configurer chaque adaptateur de données de diagnostic sélectionné pour chaque rôle, choisissez **Configurer**.

     **Exemple de rôles et d’adaptateurs de données de diagnostic :**

     Vous pouvez, par exemple, créer un rôle client nommé « Client du Bureau à distance » avec un attribut « Uses SQL » dont la valeur est « True » et un rôle serveur nommé « SQL Server » avec un attribut dont la valeur est « RAM > 16 Go ». Si vous spécifiez que le « Client du Bureau à distance » exécute les tests en choisissant **Définir en tant que rôle pour exécuter les tests** dans la page **Rôles**, le contrôleur de test sélectionne des ordinateurs qui ont des agents de test incluant l’attribut « Uses SQL » défini sur « True » pour exécuter les tests. Le contrôleur de test sélectionne également des ordinateurs SQL Server qui ont des agents de test qui incluent l’attribut « RAM > 16 Go » uniquement pour collecter des données définies par les adaptateurs de diagnostic et de données inclus dans le rôle. L'agent de test « Client bureau » peut également collecter des données pour les ordinateurs sur lesquels il s'exécute si vous sélectionnez des adaptateurs de donnée et de diagnostic pour ce rôle également.

     Pour plus d'informations sur chaque adaptateur de données de diagnostic et sur la façon de le configurer, consultez la rubrique associée qui est présentée dans le tableau ci-dessous.

     Pour plus d’informations sur les adaptateurs de données de diagnostic, consultez [collecter des informations de diagnostic à l’aide de paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptateurs de données de diagnostic pour les tests de charge**

    |Adaptateur de données de diagnostic|Utilisation dans les tests de charge|Rubrique associée|
    |-|-------------------------|-|
    |**Proxy client ASP.NET pour l’impact de test et IntelliTrace :** ce proxy permet de collecter des informations sur les appels HTTP d’un client à un serveur web pour les adaptateurs de données de diagnostic d’impact de test et IntelliTrace.|![Icône Information](../test/media/vc364f4.gif)<br /><br /> À moins que vous ayez un besoin spécifique de collecter des informations système pour les ordinateurs d'agents de test, n'incluez pas cet adaptateur. **Attention :** Nous ne recommandons pas l’utilisation de l’adaptateur IntelliTrace dans les tests de charge en raison des problèmes qui peuvent se produire à cause du volume important de données collectées. <br /><br /> Les données d'impact de test ne sont pas collectées à l'aide des tests de charge.||
    |**IntelliTrace :** Vous pouvez configurer des informations de trace de diagnostic spécifiques qui sont stockées dans un fichier journal. Un fichier journal comporte l’extension *.tdlog*. Si vous exécutez votre test et qu'une de ses étapes échoue, vous pouvez créer un bogue. Le fichier journal contenant la trace de diagnostic est automatiquement joint à ce bogue. Les données collectées dans le fichier journal augmentent l'efficacité du débogage en réduisant le temps nécessaire à la reproduction et au diagnostic d'une erreur dans le code. À partir de ce fichier journal, la session locale peut être recréée sur un autre ordinateur. Cela réduit le risque lié à l'impossibilité de reproduire un bogue.<br /><br /> Pour plus d’informations, consultez [Collecter les données IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Icône Important](../test/media/vc364f3.gif)<br /><br /> Nous ne recommandons pas l'utilisation de l'adaptateur IntelliTrace dans les tests de charge en raison des problèmes qui peuvent se produire à cause du volume important de données collectées et consignées. Vous devez essayer d'utiliser l'adaptateur IntelliTrace uniquement dans les tests de charge dont l'exécution ne dure pas longtemps et qui n'utilisent pas de nombreux agents de test.|[Guide pratique pour collecter des données IntelliTrace pour aider au débogage des problèmes difficiles](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**Profileur ASP.net :** Vous pouvez créer un paramètre de test incluant le profilage ASP.NET, qui collecte les données de performances sur les applications Web ASP.NET.|L’adaptateur de données de diagnostic du profileur ASP.NET profile le processus Internet Information Services (IIS) : il ne fonctionne donc pas avec un serveur web de développement. Pour profiler le site web dans votre test de charge, vous devez installer un agent de test sur l’ordinateur sur lequel IIS est en cours d’exécution. L'agent de test ne générera pas charge, mais sera uniquement un agent de collection. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).|[Comment : configurer ASP.NET Profiler pour les tests de charge à l’aide de paramètres de test](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Journal des événements :** vous pouvez configurer un paramètre de test pour inclure la collecte des journaux des événements, qui sera intégrée aux résultats des tests.||[Comment : configurer la collecte des journaux des événements à l’aide de paramètres de test](/previous-versions/dd504816(v=vs.110))|
    |**Émulation de réseau :** vous pouvez spécifier que vous voulez appliquer une charge réseau artificielle à votre test à l’aide d’un paramètre de test. L'émulation de réseau affecte les communications établies vers et depuis l'ordinateur en émulant une vitesse de connexion réseau particulière (par exemple, une connexion d'accès à distance). **Remarque :** L’émulation de réseau ne peut pas être utilisée pour augmenter la vitesse de connexion réseau.|L'adaptateur de l'émulation de réseau est ignoré par les tests de charge. Les tests de charge utilisent plutôt les paramètres spécifiés dans la combinaison de réseaux du scénario de test de charge.<br /><br /> Pour plus d’informations, consultez [Spécifier des types de réseaux virtuels](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informations système :** Vous pouvez configurer un paramètre de test pour inclure les informations système sur les ordinateurs où est exécuté le collecteur de données et de diagnostic des informations système. Les informations système sont spécifiées dans les résultats des tests à l'aide d'un paramètre de test.|![Icône d'informations](../test/media/vc364f4.gif)<br /><br /> Vous pouvez collecter les informations système à la fois sur les agents de charge et le système en cours de test.|Aucune configuration n'est requise pour collecter ces informations.|
    |**Impact de test :** vous pouvez collecter des informations sur les méthodes de votre code d’application utilisées lors de l’exécution d’un cas de test. Associées aux modifications apportées au code d'application par les développeurs, ces informations peuvent servir à déterminer les tests impactés par ces modifications.|Les données d'impact de test ne sont pas collectées avec les tests de charge.||
    |**Enregistreur vidéo :** vous pouvez créer un enregistrement vidéo de votre session sur le poste de travail quand vous exécutez un test automatisé. Cet enregistrement permet d'afficher les actions utilisateur associées à un test codé de l'interface utilisateur. La vidéo peut aider d'autres membres de l'équipe à isoler les problèmes liés aux applications qui sont difficiles à reproduire. **Remarque :** Quand les tests sont exécutés à distance, l’enregistreur vidéo ne fonctionne pas, sauf si l’agent s’exécute en mode interactif.|![Icône Important](../test/media/vc364f3.gif) **Avertissement :** Nous ne recommandons pas l’utilisation de l’adaptateur Enregistreur vidéo pour les tests de charge.|[Guide pratique pour inclure des enregistrements d’écran et des enregistrements vocaux pendant des tests à l’aide des paramètres de test](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Choisissez **Déploiement**.

     La page **Déploiement** s’affiche.

20. Pour créer un répertoire distinct pour le déploiement chaque fois que vous exécutez vos tests, sélectionnez **Activer le déploiement**.

    > [!NOTE]
    > Si vous sélectionnez cette option, vous pouvez continuer à générer votre application pendant l'exécution de vos tests.

21. Pour ajouter un fichier au répertoire utilisé pour l’exécution de vos tests, cliquez sur **Ajouter un fichier**, puis sélectionnez le fichier à ajouter.

    > [!NOTE]
    > Lorsque vous exécutez un test de charge, les assemblys de plug-in, les fichiers de données et les fichiers téléchargés sont déployés automatiquement.

22. Pour ajouter un répertoire au répertoire utilisé pour l’exécution de vos tests, cliquez sur **Ajouter un répertoire**, puis sélectionnez le répertoire à ajouter.

23. Pour exécuter des scripts avant et après vos tests, sélectionnez **Scripts d’installation et de nettoyage**.

     La page **Scripts d’installation et de nettoyage** s’affiche.

    1. Entrez l’emplacement du fichier de script dans **Script d’installation** ou choisissez les points de suspension (**…**) pour accéder au script d’installation.

    2. Entrez l’emplacement du fichier de script dans **Script de nettoyage** ou choisissez les points de suspension (**…**) pour accéder au script de nettoyage.

24. Pour exécuter vos tests avec un autre hôte, sélectionnez **Hôtes**.

    1. Dans **Type d’hôte**, vérifiez que **Par défaut** est sélectionné.

        > [!NOTE]
        > **ASP.NET** n’est pas pris en charge pour **Type d’hôte** dans les tests de charge.

    2. Utilisez la liste déroulante **Exécuter les tests dans un processus 32 bits ou 64 bits** pour indiquer si vous souhaitez exécuter les tests de performances web et les tests unitaires dans votre test de charge en mode 32 bits ou 64 bits.

        > [!NOTE]
        > Pour une flexibilité maximale, vous devez compiler vos projets de test de performances de site Web et de charge à l’aide de la configuration **Any CPU** . Vous pouvez ensuite les exécuter sur des agents 32 bits et 64 bits. La compilation de projets de test de performances Web et de charge à l’aide de la configuration **64 bits** n’offre aucun avantage.

25. (Facultatif) Pour limiter la durée de chaque série de tests et des tests individuels, sélectionnez **Délais d’attente des tests**.

    1. Pour abandonner l’exécution d’une série de tests quand une limite de temps est dépassée, sélectionnez **Abandonner une série de tests si la durée totale dépasse**, puis tapez une valeur pour cette limite.

    2. Pour faire échouer un test quand une limite de temps est dépassée, sélectionnez **Marquer un test comme ayant échoué si sa durée d’exécution dépasse**, puis tapez une valeur pour cette limite.

26. Ignorez **Test unitaire**. Les tests de charge n'utilisent pas ces paramètres.

27. Ignorez **Test web**. Les tests de charge n'utilisent pas ces paramètres.

28. Pour enregistrer les paramètres de test, sélectionnez **Enregistrer sous**. Tapez le nom de fichier que vous voulez dans **Nom d’objet**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Supprimer un fichier de paramètres de test de votre solution

Sous le dossier **éléments de solution** de **Explorateur de solutions**, cliquez avec le bouton droit sur les paramètres de test que vous souhaitez supprimer, puis choisissez **supprimer**.

Le fichier de paramètres de test est supprimé de votre solution.

## <a name="see-also"></a>Voir aussi

- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Collecter des informations de diagnostic avec des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)