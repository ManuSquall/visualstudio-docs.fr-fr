---
title: Configurer le profileur ASP.NET pour les tests de charge
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4f82f8f4c518a9c72399b6e28a01d112f5678c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288206"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Guide pratique pour configurer le profileur ASP.NET pour les tests de charge à l’aide de paramètres de test dans Visual Studio

Vous pouvez utiliser l’adaptateur de données de diagnostic du profileur ASP.NET pour collecter les informations du profileur ASP.NET. Cet adaptateur de données de diagnostic collecte les données de performance pour les applications ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Cet adaptateur de données de diagnostic ne peut pas être utilisé pour les tests exécutés à l’aide de Microsoft Test Manager (déconseillé dans Visual Studio 2017). Vous pouvez utiliser l’adaptateur de diagnostic du profileur ASP.NET avec les tests de charge uniquement à l’aide de sites web, ce qui nécessite Visual Studio Enterprise.

L’adaptateur de données de diagnostic du profileur ASP.NET vous permet de collecter les données du profileur ASP.NET de la couche Application quand vous exécutez un test de charge. Vous ne devez pas exécuter le profileur pour des longs tests de charge, par exemple, des tests de charge dont la durée d'exécution s'étend au-delà d'une heure. Cela tient au fait que le fichier du profileur peut devenir volumineux, peut-être des centaines de mégaoctets. Exécutez de préférence des tests de charge plus courts avec le profileur ASP.NET, qui présente l’avantage d’un outil de diagnostic approfondi des problèmes de performances.

> [!NOTE]
> L’adaptateur de données de diagnostic du profileur ASP.NET profile le processus Internet Information Services (IIS). Il ne fonctionnera donc pas sur un serveur web de développement. Pour profiler le site web dans votre test de charge, vous devez installer un agent de test sur l’ordinateur sur lequel IIS est en cours d’exécution. L'agent de test ne générera pas de charge, mais sera uniquement un agent de collection. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

Pour plus d’informations, consultez [Guide pratique pour créer un paramètre de test pour un test de charge distribué](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Configurer le profileur ASP.NET pour vos paramètres de test

Avant d’effectuer les étapes de cette procédure, vous devez ouvrir les paramètres de test depuis Visual Studio, puis sélectionner la page **Données et diagnostics**.

1. Sélectionnez le rôle à utiliser pour collecter les données du profileur ASP.NET.

    > [!WARNING]
    > Ce rôle doit être un serveur web.

2. Sélectionnez **Profileur ASP.NET** pour activer la collecte des données de profilage ASP.NET, puis choisissez **Configurer**.

     La boîte de dialogue permettant la configuration de la collection des données de profilage ASP.NET s’affiche.

3. Dans **Intervalle d’échantillonnage du profileur**, tapez une valeur indiquant le nombre de cycles d’horloge du processeur ininterrompus entre les échantillonnages de profilage ASP.NET.

4. Pour activer le profilage d’interaction de couche, sélectionnez **Activer le profilage d’interaction de couche**.

     Le profilage d’interaction de couche compte le nombre de requêtes envoyées au serveur web pour chaque artefact (par exemple, *MyPage.aspx* ou *CompanyLogo.gif*), et le temps qu’a nécessité le traitement de chaque requête. En outre, le profilage d'interaction de couche collecte les connexions ADO.NET qui ont été utilisées comme une partie de la requête de la page, et le nombre de requêtes et d'appels de procédures stockées qui ont été exécutés dans le cadre du traitement de cette requête.

     Deux ensembles différents d'informations de minutage sont collectés :

    - Informations de minutage (Min, Max, Moyenne et Total) pour le traitement de chaque requête Web.

    - Informations de minutage (Min, Max, Moyenne et Total) sur l'exécution de chaque requête.

L’adaptateur de données de diagnostic du profileur ASP.NET configuré dans votre paramètre de test vous permet maintenant de collecter des données de profilage ASP.NET sur votre application web ASP.NET.

## <a name="see-also"></a>Voir aussi

- [Collecter des informations de diagnostic avec des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)
- [Guide pratique pour créer un paramètre de test pour un test de charge distribué](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)