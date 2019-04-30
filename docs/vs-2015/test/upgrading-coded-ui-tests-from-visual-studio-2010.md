---
title: La mise à niveau des Tests codés de l’interface utilisateur
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42db6024353e3b26ddcaf6b5fa838ff791d964f4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445896"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Mise à niveau de tests codés de l'interface utilisateur à partir de Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les projets de test contenant des tests codés de l'interface utilisateur créées dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 sont réparés silencieusement quand vous les ouvrez dans Visual Studio 2012. Si les projets de test sont archivés dans le contrôle de code source, les fichiers projet sont extraits pour cette réparation. Une fois réparés, ces projets de test contenant des tests codés de l'interface utilisateur peuvent alors être utilisés à la fois dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 et [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Spécifications**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio inclut plusieurs types de projets de test. Si vous créez un test codé de l'interface utilisateur, il le sera dans un type de projet de test codé de l'interface utilisateur. Pour plus d’informations, consultez [Mise à niveau des tests à partir de versions antérieures de Visual Studio](http://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> Les projets de test[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] qui contiennent des tests codés de l'interface utilisateur doivent être régénérés quand vous ouvrez le projet de test dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ou [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] côte à côte avec [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
> Quand un projet de test qui a été créé dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] et qui contient uniquement des tests unitaires est ouvert dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], il n'est pas possible d'y ajouter des tests codés de l'interface utilisateur. De même, vous ne pouvez pas ajouter un test codé de l'interface utilisateur à un projet de test unitaire qui a été créé dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problèmes de compatibilité entre Visual Studio 2010 et Visual Studio 2012
 Le tableau suivant répertorie les problèmes à connaître en cas de migration de tests codés de l'interface utilisateur entre [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] et [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
> Il existe un problème connu lié aux références dans les projets de test codé de l'interface utilisateur qui n'apparaissent pas dans l'Explorateur de solutions. Pour plus d'informations, consultez le fichier ReadMe inclus dans le support d'installation de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

|Fonctionnalité d'interface utilisateur codée|Problème|Solution|
|----------------------------|-----------|--------------|
|Test de l'interface utilisateur Silverlight non pris en charge dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Échec de la build**<br /><br /> Si vous avez [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 et que vous avez créé des projets de test codé de l'interface utilisateur pour des applications Silverlight, ces projets ne peuvent pas être ouverts dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Nous vous recommandons de gérer ces projets dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 uniquement.|
|Test de l'interface utilisateur Firefox non pris en charge dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Réussite de la build, mais échec de la série de tests**<br /><br /> Si vous avez [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 et que vous avez créé des projets de test codé de l'interface utilisateur pour des applications web dans Firefox, ces projets ne peuvent pas être ouverts dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Nous vous recommandons de gérer ces projets dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 uniquement.|
|Nouvelles API de test de code d'interface utilisateur ajoutées dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Échec de la build**<br /><br /> Si vous créez des tests codés de l'interface utilisateur à l'aide de la nouvelle API de test de l'interface utilisateur dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ces projets ne peuvent pas être ouverts dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Vous devez gérer les projets qui utilisent la nouvelle API uniquement dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|
|Dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], des références ont été ajoutées à l'intérieur d'une instruction Choose dans le fichier csproj. Dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nous utilisons un fichier .targets de commentaires pour inclure des références d'assembly de test codé de l'interface utilisateur.|Dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], un test codé de l'interface utilisateur ne peut pas être ajouté à un projet de test créé dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (ou SP1) qui ne contenait pas de test codé de l'interface utilisateur.<br /><br /> Le processus de réparation ajoute le fichier .targets et l'instruction Choose. Si un test codé de l'interface utilisateur n'est pas dans le projet de test, alors le projet est marqué comme étant réparé et les références appropriées ne sont pas ajoutées lors de l'ajout du test codé de l'interface utilisateur dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Vous devez créer un projet de test dans la même solution à l'aide de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] et y ajouter votre nouveau test codé de l'interface utilisateur. Sinon, vous pouvez ajouter des tests codés de l'interface utilisateur au projet de test dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 et ouvrir ce projet dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

## <a name="UpgradingCodedUIFromVS2010_Update"></a> Mise à jour Visual Studio 2010 SP1
 Une mise à jour de [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 compatible avec Visual Studio 2012 et Windows 8 est disponible en téléchargement dans le [Centre de téléchargement Microsoft](http://www.microsoft.com/download/details.aspx?id=34677) , ainsi qu’en tant que mise à jour de Visual Studio.

 Après avoir appliqué la mise à jour, les fonctionnalités d'outil de test codé de l'interface utilisateur [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 suivantes sont améliorées pour Windows 8 :

- Vous pouvez exécuter un test codé de l'interface utilisateur pour des contrôles Windows Presentation Foundation (WPF) basés sur le basé sur le Microsoft .NET Framework 4.5 sur un ordinateur qui exécute Windows 8.

- Vous pouvez exécuter un test codé de l'interface utilisateur pour Internet Explorer 10 64 bits (x64) sur un ordinateur qui exécute Windows 8.

  La mise à jour contient également des correctifs pour les problèmes suivants :

- **Couverture du code :** Impossibilité d’ouvrir un fichier de couverture du code (.coverage) créé par Visual Studio 2012 dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Artefacts de test bloqués :** Votre équipe dispose d’un artefact de test qui est affecté à un utilisateur non valide dans Team Foundation Server (TFS) 2010. Par exemple, un utilisateur a quitté l'entreprise, mais un cas de test lui est toujours assigné. Vous mettez à niveau TFS 2010 vers TFS 2012. Vous utilisez [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 pour vous connecter au serveur TFS mis à niveau. Vous n'êtes pas en mesure d'assigner l'artefact de test à l'un des utilisateurs TFS à l'aide de [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Test de charge :** Lorsque vous exécutez un test de charge avec un type de réseau autre que le profil de réseau local (LAN) sur un ordinateur qui exécute Windows 8, le pilote d’émulateur réseau entraîne une défaillance du système d’exploitation. Pour plus d’informations, consultez [l’article 2736182 de la Base de connaissances](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Voir aussi
 [Portage, migration et la mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [la mise à niveau des Tests à partir de Versions antérieures de Visual Studio](http://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [utiliser UI Automation pour tester votre Code](../test/use-ui-automation-to-test-your-code.md) [générant un Contrôleur de test à partir d’un enregistrement des actions existant](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [prise en charge des plateformes et Configurations pour les Tests codés de l’interface utilisateur t enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
