---
title: Améliorer les performances d’un complément VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7529c69270b5f33cde32e8a7907f1b80589c43b7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "92298512"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Améliorer les performances d’un complément VSTO
  Vous pouvez offrir aux utilisateurs une meilleure expérience. En effet, en optimisant les compléments VSTO que vous créez pour les applications Office, vous pouvez leur permettre d’être plus rapides pour démarrer, arrêter, ouvrir des éléments et exécuter d’autres tâches. Si vous créez un complément VSTO pour Outlook, vous pouvez également réduire les risques de désactivation du complément VSTO en raison de performances insuffisantes. Pour améliorer les performances du complément VSTO, vous pouvez implémenter les stratégies suivantes :

- [Charger les compléments VSTO à la demande](#Load)

- [Publier les solutions Office à l'aide de Windows Installer](#Publish)

- [Ignorer la réflexion du ruban](#Bypass).

- [Effectuer les opérations coûteuses dans un thread d'exécution distinct](#Perform)

  Pour plus d’informations sur l’optimisation d’un complément VSTO Outlook, consultez [critères de performances pour conserver les compléments VSTO activés](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> Charger les compléments VSTO à la demande
 Vous pouvez configurer un complément VSTO pour qu’il se charge uniquement dans les cas suivants :

- la première fois que l’utilisateur démarre l’application après l’installation du complément VSTO ;

- la première fois que l’utilisateur interagit avec le complément VSTO après un nouveau démarrage de l’application.

  Par exemple, votre complément VSTO peut remplir une feuille de calcul avec des données quand l’utilisateur choisit un bouton personnalisé nommé **obtenir mes données**. L’application doit charger votre complément VSTO au moins une fois pour que le bouton **Afficher mes données** puisse apparaître dans le ruban. Toutefois, le complément VSTO n’est pas rechargé lorsque l’utilisateur démarre l’application la prochaine fois. Il se charge uniquement quand l’utilisateur choisit le bouton **Obtenir mes données** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution ClickOnce visant à charger les compléments VSTO à la demande

1. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

2. Dans la barre de menus, choisissez **Afficher**les  >  **pages de propriétés**.

3. Sous l'onglet **Publier** , choisissez le bouton **Options** .

4. Dans la boîte de dialogue **Options de publication** , sélectionnez l'élément de liste **Paramètres Office** , choisissez l'option **Charger à la demande** , puis choisissez le bouton **OK** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution Windows Installer visant à charger les compléments VSTO à la demande

1. Dans le registre, définissez l' `LoadBehavior` entrée de la clé ** _racine_\Software\Microsoft\Office \\ _applicationName_\Addins \\ _Add-in ID_ ** sur **0x10**.

     Pour plus d’informations, consultez [entrées du Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Pour configurer une solution visant à charger les compléments VSTO à la demande pendant le débogage de la solution

1. Créez un script qui définit l' `LoadBehavior` entrée de la clé ** _racine_de l' \\ ID du \\ _complément_ \Software\Microsoft\Office_applicationName_\Addins** sur **0x10**.

     Le code ci-dessous est un exemple de ce script.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Créez un événement post-build qui met à jour le Registre en utilisant le script.

     Le code suivant est un exemple d'une chaîne de commande que vous pouvez ajouter à un événement post-build.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Pour plus d’informations sur la création d’un événement après génération dans un projet C#, consultez [Guide pratique pour spécifier des événements de build &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Pour plus d’informations sur la création d’un événement après génération dans un projet de Visual Basic, consultez [Guide pratique pour spécifier des événements de build &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> Publier des solutions Office à l’aide de Windows Installer
 Si vous publiez votre solution à l’aide de Windows Installer, Visual Studio 2010 Tools pour Office Runtime ignore les étapes suivantes lors du chargement du complément VSTO.

- Validation du schéma manifeste

- Recherche automatique des mises à jour

- Validation des signatures numériques des manifestes de déploiement

  > [!NOTE]
  > Cette approche n’est pas nécessaire si vous déployez votre complément VSTO à un emplacement sécurisé sur les ordinateurs des utilisateurs.

  Pour plus d’informations, consultez [déployer une solution Office à l’aide de Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Ignorer la réflexion du ruban
 Si vous générez une solution à l’aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , assurez-vous que vos utilisateurs ont installé la version la plus récente de Visual Studio 2010 Tools pour Office Runtime lorsque vous déployez la solution. Les versions antérieures du runtime VSTO sont reflétées dans les assemblys de solution pour localiser les personnalisations du ruban. Ce processus peut ralentir le chargement du complément VSTO.

 Vous pouvez également empêcher toute version de Visual Studio 2010 Tools pour Office Runtime d’utiliser la réflexion pour identifier les personnalisations du ruban. Pour suivre cette stratégie, substituez la `CreateRibbonExtensibility` méthode et retournez explicitement les objets ruban. Si votre complément VSTO ne contient pas de personnalisations de ruban, retournez `null` à l’intérieur de la méthode.

 L’exemple suivant retourne un objet ruban en fonction de la valeur d’un champ.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Effectuer des opérations coûteuses dans un thread d’exécution distinct
 Prévoyez d'effectuer les tâches qui prennent du temps (par exemple, les tâches longues, les connexions de base de données ou autres sortes d'appels réseau) dans un thread distinct. Pour plus d’informations, consultez [prise en charge des threads dans Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Tout le code qui appelle le modèle objet Office doit s'exécuter dans le thread principal.

## <a name="see-also"></a>Voir aussi

- [Compléments VSTO de chargement à la demande](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Delay-loading the CLR in Office Add-ins](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Créer des compléments VSTO pour Office à l'aide de Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)