---
title: Étendre des tests codés de l’interface utilisateur et des enregistrements des actions
description: Découvrez comment créer une extension de l’infrastructure de test codé de l’interface utilisateur pour votre interface utilisateur spécifique en tirant parti de l’extensibilité de l’infrastructure de test codé de l’interface utilisateur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8c4a846fe9425af7dc62ef93276c0272f480b7f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949868"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Étendre des tests codés de l’interface utilisateur et des enregistrements des actions

L'infrastructure de test pour les tests codés de l'interface utilisateur et les enregistrements des actions ne prend pas en charge toutes les interfaces utilisateur possibles. Elle risque de ne pas prendre en charge l’interface utilisateur spécifique que vous souhaitez tester. Par exemple, vous ne pouvez pas créer immédiatement un test codé de l’interface utilisateur ou un enregistrement des actions pour une feuille de calcul Microsoft Excel. Toutefois, vous pouvez créer votre propre extension de l'infrastructure de test codé de l'interface utilisateur, qui prend en charge votre interface utilisateur spécifique en tirant parti de l’extensibilité du framework de test codé de l'interface utilisateur.

![Architecture du test IU](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Exemple d’extension pour tester Microsoft Excel

Ce [billet de blog](/archive/blogs/gautamg/3-introducing-sample-excel-extension) contient un lien vers un [exemple d’extension](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) de framework de test codé de l’interface utilisateur. Vous pouvez également voir l’intégralité de la [série de billets de blog sur l’extensibilité du test codé de l'interface utilisateur](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility).

> [!NOTE]
> L'exemple est conçu pour être utilisé avec Microsoft Excel 2010. Il peut fonctionner ou pas avec d’autres versions d’Excel.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Meilleures pratiques pour les tests codés de l’interface utilisateur](../test/best-practices-for-coded-ui-tests.md)
- [Configurations et plateformes prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)