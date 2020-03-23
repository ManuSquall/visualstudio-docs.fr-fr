---
title: Améliorer les performances d’un add-in VSTO
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
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416547"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Améliorer les performances d’un add-in VSTO
  Vous pouvez offrir aux utilisateurs une meilleure expérience. En effet, en optimisant les compléments VSTO que vous créez pour les applications Office, vous pouvez leur permettre d’être plus rapides pour démarrer, arrêter, ouvrir des éléments et exécuter d’autres tâches. Si vous créez un complément VSTO pour Outlook, vous pouvez également réduire les risques de désactivation du complément VSTO en raison de performances insuffisantes. Pour améliorer les performances du complément VSTO, vous pouvez implémenter les stratégies suivantes :

- [Charger les compléments VSTO à la demande](#Load)

- [Publier les solutions Office à l'aide de Windows Installer](#Publish)

- [Réflexion de ruban de déviation](#Bypass).

- [Effectuer les opérations coûteuses dans un thread d'exécution distinct](#Perform)

  Pour plus d’informations sur la façon d’optimiser un Add-in Outlook VSTO, consultez [les critères de performance pour garder VSTO Add-ins activé](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>Chargez les add-ins VSTO sur demande
 Vous pouvez configurer un complément VSTO pour qu’il se charge uniquement dans les cas suivants :

- la première fois que l’utilisateur démarre l’application après l’installation du complément VSTO ;

- la première fois que l’utilisateur interagit avec le complément VSTO après un nouveau démarrage de l’application.

  Par exemple, votre add-in VSTO peut remplir une feuille de travail avec des données lorsque l’utilisateur choisit un bouton personnalisé qui est étiqueté **Get My Data**. L’application doit charger votre ADD-in VSTO au moins une fois afin que le bouton **Get My Data** puisse apparaître dans le ruban. Toutefois, l’add-in VSTO ne se charge pas à nouveau lorsque l’utilisateur démarre l’application la prochaine fois. Il se charge uniquement quand l’utilisateur choisit le bouton **Obtenir mes données** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution ClickOnce visant à charger les compléments VSTO à la demande

1. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

2. Sur la barre de menu, choisissez **Voir les** > **pages de propriété**.

3. Sous l'onglet **Publier** , choisissez le bouton **Options** .

4. Dans la boîte de dialogue **Options de publication** , sélectionnez l'élément de liste **Paramètres Office** , choisissez l'option **Charger à la demande** , puis choisissez le bouton **OK** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution Windows Installer visant à charger les compléments VSTO à la demande

1. Dans le registre, `LoadBehavior` définissez l’entrée de la ** _clé_d’identification Root 'Software’Microsoft’Office\\_ApplicationName_'Addins Addins\\Add-in ID** à **0x10**.

     Pour plus d’informations, voir [les inscriptions au Registre des add-ins VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Pour configurer une solution visant à charger les compléments VSTO à la demande pendant le débogage de la solution

1. Créez un script `LoadBehavior` qui définit l’entrée de la ** _clé_d’identification Root 'Software’Microsoft’Office\\_ApplicationName_'Addins Addins\\Add-in ID** à **0x10**.

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

     Pour plus d’informations sur la façon de créer un événement post-construction dans le cadre d’un projet C, voir [comment : Spécifier des événements de construction &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Pour plus d’informations sur la façon de créer un événement post-construction dans un projet de base visuelle, voir [Comment: Spécifier construire des événements &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Publier des solutions Office en utilisant Windows Installer
 Si vous publiez votre solution en utilisant Windows Installer, les outils Visual Studio 2010 pour l’exécution Office contournent les étapes suivantes lorsque les charges VSTO Add-in.

- Validation du schéma manifeste

- Recherche automatique des mises à jour

- Validation des signatures numériques des manifestes de déploiement

  > [!NOTE]
  > Cette approche n’est pas nécessaire si vous déployez votre add-in VSTO à un emplacement sécurisé sur les ordinateurs des utilisateurs.

  Pour plus d’informations, voir [Déployez une solution Office en utilisant Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Réflexion de ruban de déviation
 Si vous construisez [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]une solution en utilisant, assurez-vous que vos utilisateurs ont installé la version la plus récente des outils Visual Studio 2010 pour l’exécution Office lorsque vous déployez la solution. Les anciennes versions du temps d’exécution VSTO reflétées dans des assemblages de solutions pour localiser les personnalisations de ruban. Ce processus peut ralentir le chargement du complément VSTO.

 Comme alternative, vous pouvez empêcher n’importe quelle version du Visual Studio 2010 Tools for Office runtime d’utiliser la réflexion pour identifier les personnalisations de ruban. Pour suivre cette stratégie, `CreateRibbonExtensibility` remplacez la méthode et retournez explicitement les objets Ruban. Si votre add-in VSTO ne contient pas de `null` personnalisations de ruban, retournez à l’intérieur de la méthode.

 L’exemple suivant renvoie un objet Ruban basé sur la valeur d’un champ.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Effectuer des opérations coûteuses dans un fil d’exécution séparé
 Prévoyez d'effectuer les tâches qui prennent du temps (par exemple, les tâches longues, les connexions de base de données ou autres sortes d'appels réseau) dans un thread distinct. Pour plus d’informations, voir [le support Threading dans Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Tout le code qui appelle le modèle objet Office doit s'exécuter dans le thread principal.

## <a name="see-also"></a>Voir aussi

- [Add-ins VSTO de chargement de la demande](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Delay-loading the CLR in Office Add-ins](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Créer des compléments VSTO pour Office à l'aide de Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
