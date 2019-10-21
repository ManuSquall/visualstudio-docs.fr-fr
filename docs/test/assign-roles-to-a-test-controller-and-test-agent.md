---
title: Rôles de contrôleur de test et d’agent de test pour les tests automatisés
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9ae46db2d99024b598ff655452ca748298b528a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665301"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Assigner des rôles à un contrôleur de test et à un agent de test

Cet article montre comment créer et configurer un paramètre de test qui utilise un contrôleur de test et un agent de test pour distribuer des tests sur plusieurs ordinateurs en utilisant Visual Studio. Il indique également comment ajouter des adaptateurs de diagnostic et de données au paramètre de test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Configuration requise

- Créez des tests unitaires ou des tests codés de l'interface utilisateur à exécuter avec le paramètre de test.

- Installez un contrôleur de test et des agents de test. Pour plus d’informations sur la façon d’installer un contrôleur de test et des agents de test, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Pour créer et configurer un paramètre de test

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Éléments de solution**, pointez sur **Ajouter**, puis choisissez **Nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2. Dans le volet **Modèles installés**, choisissez **Paramètres de test**.

3. Dans la zone **Nom**, tapez **TestSettingDistributedTestWalkthrough**.

4. Sélectionnez **Ajouter**.

     Le nouveau fichier de test *TestSettingDistributedTestWalkthrough.testsettings* s’affiche dans **l’Explorateur de solutions**, sous le dossier **Éléments de solution**.

     La boîte de dialogue **Paramètres de test** s’affiche. La page **Général** est sélectionnée.

     Vous pouvez maintenant modifier et enregistrer des valeurs de paramètres de test.

5. Sous **Nom**, tapez le nom des paramètres de test.

6. Sous **Description**, tapez **Paramètres de test distribués**.

7. Laissez l’option **Schéma d’affectation de noms par défaut** sélectionnée.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Pour assigner des rôles à un contrôleur de test et des agents de test

1. Choisissez **Rôles**.

     La page **Rôles** s’affiche.

2. Pour exécuter votre test à distance, utilisez la liste déroulante **Méthode d’exécution des tests** et sélectionnez **Exécution distante**.

3. Dans la liste déroulante **Contrôleur**, tapez le nom d’ordinateur de votre [contrôleur de test](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Si vous ajoutez un contrôleur pour la première fois, aucun contrôleur n'est répertorié dans la liste déroulante. La liste est remplie par les contrôleurs précédents que vous avez définis dans d'autres paramètres de test.

4. Sous **Rôles**, choisissez **Ajouter**.

5. Dans la ligne en surbrillance sous la colonne **Nom**, tapez **Test distribué**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Pour assigner un adaptateur de diagnostic et de données à votre paramètre de test

1. Choisissez **Données et diagnostics**.

     La page **Données et diagnostics** s’affiche.

2. Sous **Rôle**, vérifiez si le rôle **Test distribué** est sélectionné.

3. Sous **Données et diagnostics pour le rôle sélectionné**, sélectionnez les adaptateurs **IntelliTrace** et **Informations système**.

     Pour plus d’informations sur ces adaptateurs et d’autres adaptateurs que vous pouvez utiliser dans un paramètre de test, consultez [Configurer des tests unitaires](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Choisissez **Hôtes**.

5. Si votre ordinateur s’exécute sous une version 64 bits de Microsoft Windows, et que vous avez compilé votre test à l’aide de la configuration **Any CPU**, utilisez la liste déroulante **Exécuter les tests dans un processus 32 bits ou 64 bits** et sélectionnez **Exécuter les tests dans un processus 64 bits sur un ordinateur 64 bits**.

    > [!TIP]
    > Pour une flexibilité maximale, vous devez compiler vos projets de test avec la configuration **Any CPU**. Vous pouvez ensuite les exécuter sur des agents 32 bits et 64 bits. La compilation de projets de test avec la configuration **64 bits** ne présente aucun avantage particulier.

6. Pour enregistrer les nouveaux paramètres de test, choisissez **Appliquer**.

7. Choisissez **Fermer**.

::: moniker range="vs-2017"

8. Dans le menu **test** , sélectionnez **paramètres de test** > **Sélectionnez fichier de paramètres de test** , puis choisissez le fichier *TestSettingDistributedTestWalkthrough. testsettings* .

::: moniker-end

::: moniker range=">=vs-2019"

8. Dans le menu **test** , choisissez **Sélectionner le fichier de paramètres**. Accédez au fichier *TestSettingDistributedTestWalkthrough.testsettings* et sélectionnez le.

::: moniker-end

9. Exécutez votre test conformément à la procédure habituelle.

     Lorsque le contrôleur de test traite des tests unitaires et des tests codés de l'interface utilisateur, il divise les tests en groupes de 100 et les envoie à un ordinateur d'agent de test. Par exemple, si vous avez 250 tests unitaires et trois agents de test, les 100 premiers tests unitaires sont envoyés à agent1, les 100 tests unitaires suivants sont envoyés à agent2 et les 50 tests unitaires restants sont envoyés à agent3.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)