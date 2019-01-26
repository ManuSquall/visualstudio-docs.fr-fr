---
title: Améliorer les performances d’un composant logiciel complément VSTO
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
ms.openlocfilehash: a06022075086ad4792d35761c3af0e14f8f96e56
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867466"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Améliorer les performances d’un complément VSTO
  Vous pouvez offrir aux utilisateurs une meilleure expérience. En effet, en optimisant les compléments VSTO que vous créez pour les applications Office, vous pouvez leur permettre d’être plus rapides pour démarrer, arrêter, ouvrir des éléments et exécuter d’autres tâches. Si vous créez un complément VSTO pour Outlook, vous pouvez également réduire les risques de désactivation du complément VSTO en raison de performances insuffisantes. Pour améliorer les performances du complément VSTO, vous pouvez implémenter les stratégies suivantes :

- [Charger les compléments VSTO à la demande](#Load)

- [Publier les solutions Office à l'aide de Windows Installer](#Publish)

- [Ignorer la réflexion du ruban](#Bypass).

- [Effectuer les opérations coûteuses dans un thread d'exécution distinct](#Perform)

  Pour plus d’informations sur comment optimiser un complément VSTO Outlook dans, consultez [critères de performances pour maintenir les Compléments VSTO activés](http://go.microsoft.com/fwlink/?LinkID=266503).

##  <a name="Load"></a> Charger les compléments VSTO à la demande
 Vous pouvez configurer un complément VSTO pour qu’il se charge uniquement dans les cas suivants :

- la première fois que l’utilisateur démarre l’application après l’installation du complément VSTO ;

- la première fois que l’utilisateur interagit avec le complément VSTO après un nouveau démarrage de l’application.

  Par exemple, votre complément, VSTO peut remplir une feuille de calcul avec des données lorsque l’utilisateur choisit un bouton personnalisé appelé **obtenir mes données**. L’application doit charger votre complément, VSTO au moins une fois afin que le **obtenir mes données** bouton peut apparaître dans le ruban. Toutefois, le composant logiciel complément VSTO ne charge à nouveau lorsque l’utilisateur démarre l’application de la prochaine fois. Il se charge uniquement quand l’utilisateur choisit le bouton **Obtenir mes données** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution ClickOnce visant à charger les compléments VSTO à la demande

1.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

2.  Dans la barre de menus, sélectionnez **Afficher** > **Pages de propriétés**.

3.  Sous l'onglet **Publier** , choisissez le bouton **Options** .

4.  Dans la boîte de dialogue **Options de publication** , sélectionnez l'élément de liste **Paramètres Office** , choisissez l'option **Charger à la demande** , puis choisissez le bouton **OK** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution Windows Installer visant à charger les compléments VSTO à la demande

1.  Dans le Registre, définissez la `LoadBehavior` entrée de la **_racine_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _ID du complément_** clé **0 x 10**.

     Pour plus d’informations, consultez [les entrées de Registre pour les Compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Pour configurer une solution visant à charger les compléments VSTO à la demande pendant le débogage de la solution

1.  Créer un script qui définit le `LoadBehavior` entrée de la **_racine_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _ID du complément_** clé **0 x 10**.

     Le code ci-dessous est un exemple de ce script.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2.  Créez un événement post-build qui met à jour le Registre en utilisant le script.

     Le code suivant est un exemple d'une chaîne de commande que vous pouvez ajouter à un événement post-build.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Pour plus d’informations sur la création d’événement post-build dans un C# de projet, consultez [Comment : Spécifier les événements de build &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Pour plus d’informations sur la création d’un événement post-build dans un projet Visual Basic, consultez [Comment : Spécifier les événements de build &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

##  <a name="Publish"></a> Publier les solutions Office à l’aide du programme d’installation de Windows
 Si vous publiez votre solution à l’aide du programme d’installation de Windows, Visual Studio 2010 Tools pour Office runtime ignore les étapes suivantes pendant le VSTO Add-in charge.

- Validation du schéma manifeste

- Recherche automatique des mises à jour

- Validation des signatures numériques des manifestes de déploiement

  > [!NOTE]
  >  Cette approche n’est pas nécessaire si vous déployez votre complément, VSTO à un emplacement sécurisé sur les ordinateurs des utilisateurs.

  Pour plus d’informations, consultez [déployer une solution Office à l’aide du programme d’installation de Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

##  <a name="Bypass"></a> Ignorer la réflexion du ruban
 Si vous générez une solution à l’aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], vérifiez que vos utilisateurs ont installé la version la plus récente de Visual Studio 2010 Tools pour Office runtime lorsque vous déployez la solution. Les versions antérieures de ce runtime répercutées dans les assemblys de la solution pour localiser les personnalisations du ruban. Ce processus peut ralentir le chargement du complément VSTO.

 Comme alternative, vous pouvez empêcher n’importe quelle version de Visual Studio 2010 Tools pour Office runtime utilisent la réflexion pour identifier les personnalisations du ruban. Pour suivre cette stratégie, substituez le `CreateRibbonExtensibility` méthode et retournez explicitement les objets ruban. Si votre complément, VSTO ne contient pas toutes les personnalisations du ruban, retournez `null` à l’intérieur de la méthode.

 L’exemple suivant retourne un objet de ruban en fonction de la valeur d’un champ.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

##  <a name="Perform"></a> Effectuer les opérations coûteuses dans un thread d’exécution distinct
 Prévoyez d'effectuer les tâches qui prennent du temps (par exemple, les tâches longues, les connexions de base de données ou autres sortes d'appels réseau) dans un thread distinct. Pour plus d’informations, consultez [Threading prise en charge dans Office](../vsto/threading-support-in-office.md).

> [!NOTE]
>  Tout le code qui appelle le modèle objet Office doit s'exécuter dans le thread principal.

## <a name="see-also"></a>Voir aussi

- [Compléments VSTO de chargement de la demande](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Le CLR dans des compléments Office à chargement différé](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Créer des Compléments VSTO pour Office à l’aide de Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
