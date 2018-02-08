---
title: "FAQ concernant l’Explorateur de tests | Microsoft Docs"
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: ghogen
ms.openlocfilehash: db3cf85576e6c46aca14897f7244cd0f56d8d5c2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-test-explorer-faq"></a>FAQ concernant l’Explorateur de tests Visual Studio

## <a name="test-discovery"></a>Découverte de tests

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1. L’Explorateur de tests ne découvre pas mes tests qui contiennent des théories, des adaptateurs personnalisés ou des caractéristiques personnalisés, qui utilisent des instructions #ifdef ou qui sont définis dynamiquement. Comment puis-je découvrir ces tests ?

  Générez votre projet et vérifiez que la découverte basée sur les assemblys est activée sous **Outils > Options > Test**.

  La [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824), qui est la découverte de tests basée sur les sources, ne peut pas découvrir les tests qui contiennent des théories, des adaptateurs personnalisés ou des caractéristiques personnalisés, qui utilisent des instructions `#ifdef` ou qui sont définis dynamiquement. Une build est nécessaire pour découvrir correctement ces tests. Dans les préversions 15.6, la découverte basée sur les assemblys (le découvreur traditionnel) s’exécute uniquement après les builds. En d’autres termes, la découverte de tests en temps réel découvre autant de tests que possible au fur et à mesure que vous effectuez des modifications, et la découverte basée sur les assemblys permet de faire apparaître des théories (ou tout autre test défini dynamiquement) après une build. La découverte de tests en temps réel améliore la réactivité, tout en vous permettant d’obtenir des résultats complets et précis après une build.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Que signifie le signe plus (+) qui apparaît sur la ligne supérieure l’Explorateur de tests ?

  Le signe plus (+) indique que d’autres tests peuvent être découverts après une build si la découverte basée sur les assemblys est activée. Il apparaît si des tests définis dynamiquement sont détectés dans votre projet.

  ![Signe plus sur la ligne de résumé](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. La découverte basée sur les assemblys ne fonctionne plus avec mon projet. Comment puis-je la réactiver ?

  Accédez à **Outils > Options > Test** et cochez la case **Découvrez également les tests des assemblys générés après les builds**.

  ![Option basée sur les assemblys](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Les tests s’affichent désormais automatiquement dans l’Explorateur de tests quand j’écris, sans que j’aie à générer mon projet. Que s’est-il passé ?

  Cette fonctionnalité s’appelle la [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824). Elle utilise un analyseur Roslyn pour découvrir les tests et renseigner l’Explorateur de tests en temps réel, sans que l’utilisateur ait à générer son projet. Pour plus d’informations sur le comportement de la découverte de tests pour les tests définis dynamiquement tels que les théories ou les caractéristiques personnalisées, consultez le FAQ nº 1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Quels langages et quelles infrastructures de test peuvent utiliser la découverte de tests en temps réel ?

  La [découverte de tests en temps réel](https://go.microsoft.com/fwlink/?linkid=862824) fonctionne uniquement avec les langages managés (C# et Visual Basic), car elle utilise le compilateur Roslyn. À l’heure actuelle, la découverte de test en temps réel fonctionne uniquement avec les infrastructures xUnit, NUnit et MSTest.

## <a name="features"></a>Fonctionnalités

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Comment puis-je activer les indicateurs de fonctionnalités pour tester les nouvelles fonctionnalités de test ?

Les indicateurs de fonctionnalités servent à fournir des parties expérimentales ou inachevées du produit à des utilisateurs passionnés qui souhaitent envoyer des commentaires avant le lancement officiel des fonctionnalités. Ils peuvent affecter votre expérience IDE. Il est recommandé de les utiliser uniquement dans des environnements de développement sécurisés, tels que des machines virtuelles. Les indicateurs de fonctionnalités sont toujours des paramètres que vous utilisez à vos risques et périls. Vous pouvez activer les fonctionnalités expérimentales à l’aide de l’[extension Feature Flags](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) ou de l’invite de commandes développeur.

![Extension Feature Flag](media/testex-featureflag.png)

Pour activer un indicateur de fonctionnalité à l’aide de l’invite de commandes développeur Visual Studio, utilisez la commande suivante. Modifiez le chemin d’accès à l’emplacement d’installation de Visual Studio sur votre ordinateur et modifiez la clé de Registre en fonction de l’indicateur de fonctionnalité souhaité.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Vous pouvez désactiver l’indicateur à l’aide de la même commande, en utilisant la valeur 0 au lieu de 1 après dword.
  
## <a name="see-also"></a>Voir aussi

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[Création et exécution des tests unitaires pour le code existant](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[Tests unitaires sur votre code](unit-test-your-code.md)
[Questions fréquentes concernant Live Unit Testing](live-unit-testing-faq.md)
