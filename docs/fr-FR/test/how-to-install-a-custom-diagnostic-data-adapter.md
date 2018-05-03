---
title: Guide pratique pour installer un adaptateur de données de diagnostic personnalisé dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24ce9f954164cd8d243edfab4387f6b174c0648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>Comment : installer un adaptateur de données de diagnostic personnalisé

Si vous avez créé un adaptateur de données de diagnostic personnalisé ou qu'un tel adaptateur vous a été fourni, vous pouvez installer votre assembly d'adaptateur de données de diagnostic en copiant le fichier d'assembly correspondant dans le répertoire approprié de votre ordinateur local.

 Si vous souhaitez employer votre adaptateur de données de diagnostic personnalisé pour un rôle dans un environnement, vous devez l'installer sur tous les ordinateurs exécutant des agents de test qui sont susceptibles d'être utilisés pour ce rôle.

 Utilisez la procédure suivante pour installer votre adaptateur de diagnostic personnalisé dans les emplacements appropriés. Vous devez disposer d'autorisations d'administration sur l'ordinateur où vous installez l'adaptateur de données de diagnostic.

## <a name="installing-a-custom-diagnostic-data-adapter"></a>Installation d'un adaptateur de données de diagnostic personnalisé

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>Pour installer un adaptateur de données de diagnostic personnalisé

1.  Pour utiliser l’adaptateur de données de diagnostic lorsque vous exécutez des tests sur votre ordinateur client ou sur un ordinateur agent, copiez tous les fichiers de votre répertoire de build vers le répertoire suivant sur l’ordinateur cible en fonction du chemin d’accès d’installation :

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     Fichiers à copier :

    -   Assembly d'adaptateur de données de diagnostic (.dll) (obligatoire)

    -   Fichier de données de débogage (.pdb) pour votre adaptateur (facultatif)

    -   Fichier de configuration pour votre adaptateur (`<diagnostic data adapter name>.dll.config`), si vous avez des paramètres de configuration par défaut (facultatif)

    -   Assembly de l'éditeur de configuration, si vous l'avez créé, pour modifier les paramètres de configuration de l'adaptateur (facultatif) Cela concerne uniquement les ordinateurs clients. Les ordinateurs agents n'utilisent pas l'éditeur.

    > [!NOTE]
    > Bien que votre adaptateur de données de diagnostic et votre éditeur de configuration puissent être créés dans le même projet et générés dans le même assembly, vous pouvez utiliser des projets distincts et créer des assemblys séparés, si tel est votre choix.

     Pour plus d’informations sur la configuration de vos paramètres de test pour l’utilisation d’un environnement durant l’exécution de vos tests, consultez [Collecter des données de diagnostic dans les tests manuels (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

2.  Pour sélectionner votre adaptateur de données de diagnostic pour un test, vous devez d’abord sélectionner les paramètres d’un test existant, ou en créer un à partir de Test Manager ou de Visual Studio, puis sélectionner votre adaptateur de données de diagnostic sous l’onglet **Données et diagnostics** des paramètres du test sélectionné.

3.  Si vous avez créé et installé un éditeur de configuration d’adaptateur de données de diagnostic, choisissez **Configurer** en regard de votre adaptateur et apportez les éventuelles modifications nécessaires afin de configurer ce dernier pour vos paramètres de test. Choisissez ensuite **Enregistrer**. Pour plus d’informations sur la création d’un éditeur de configuration pour votre collecteur de données de diagnostic, consultez [Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

4.  Si vous exécutez vos tests à partir de Microsoft Test Manager, vous pouvez affecter ces paramètres de test à votre plan de test avant d’exécuter vos tests, ou utiliser la commande **Exécuter avec des options** pour affecter et remplacer des paramètres de test. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

     Si vous exécutez vos tests à partir de Visual Studio, vous devez définir ces paramètres de test comme étant actifs. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

5.  Exécutez vos tests à l'aide des paramètres de test, en sélectionnant l'adaptateur de données de diagnostic.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un adaptateur de données de diagnostic](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Exemple de projet pour la création d’un adaptateur de données de diagnostic](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Création d’un adaptateur de données de diagnostic pour collecter des données personnalisées ou affecter un ordinateur de test](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)