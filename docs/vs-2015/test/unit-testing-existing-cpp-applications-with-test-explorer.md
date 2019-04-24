---
title: Réalisation de tests unitaires d’applications C++ existantes avec l’Explorateur de tests | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2558ec2c222bf07ad23c1d00fb3d99b4de5d9f25
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087441"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Applications C++ existantes de tests unitaires avec Test Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nous vous recommandons, avant de modifier une application existante, de vérifier qu'elle a une bonne couverture de tests unitaires. Vous êtes ainsi sûr que vos modifications n'ont pas introduit de bogues. Si l'application n'a pas encore de tests unitaires, vous pouvez les ajouter à l'aide des techniques expliquées dans cette rubrique. Cette rubrique décrit comment ajouter des tests unitaires pour du code Visual C++ existant, en commençant par choisir comment tester votre code, puis en créant, écrivant et enfin exécutant les tests.  
  
## <a name="deciding-how-to-test-your-code"></a>Décider comment tester votre code  
 Ouvrez le projet C++ existant, et examinez-le pour déterminer comment ajouter les tests unitaires. Vous pouvez utiliser des outils de modélisation, qui vous permettent d'afficher les dépendances du code et vous aident à comprendre comment les parties interagissent. Pour plus d’informations, consultez [Visualiser le code](../modeling/visualize-code.md).  
  
 Nous vous recommandons de répartir vos modifications en petites tâches. Avant chaque petite modification, écrivez des tests unitaires pour les aspects du comportement qui resteront identiques. Lorsque vous avez effectué la modification, ces tests continuent de réussir. Par exemple, si vous envisagez de modifier une fonction de tri pour qu'elle trie une liste de personnes par le nom au lieu du prénom, vous pouvez écrire un test unitaire qui vérifie que tous les noms d'entrée apparaissent dans la sortie. Après avoir apporté la modification, vous pouvez ajouter de nouveaux tests unitaires pour le nouveau comportement.  
  
 S'il est pratique, une grande partie ou la totalité de vos tests unitaires doivent utiliser uniquement les fonctions qui sont exportées. Toutefois, si vous modifiez simplement une petite partie de l'application, vous pouvez utiliser les fonctions qui ne sont pas exportées. Par exemple, vous pouvez avoir besoin de tests qui appellent des fonctions internes ou qui définissent et obtiennent les valeurs des variables internes.  
  
 Il existe plusieurs façons de tester le code du produit, selon qu'il expose les interfaces que vous souhaitez tester. Choisissez l'un des moyens suivants :  
  
 **Les tests unitaires utilisent uniquement les fonctions exportées à partir du code testé :**  
 Ajoutez un projet de test distinct. Dans ce projet de test, ajoutez une référence au projet testé.  
  
 Passez à la procédure [Pour référencer des fonctions exportées depuis le projet de test](#projectRef).  
  
 **Le code testé est généré sous la forme d’un fichier .exe :**  
 Ajoutez un projet de test distinct. Liez-le au fichier objet de sortie.  
  
 Passez à la procédure [Pour lier les tests aux fichiers objets ou bibliothèques](#objectRef).  
  
 **Les tests unitaires doivent utiliser des données et des fonctions privées, et le code testé peut être établi comme bibliothèque statique :**  
 Modifiez le projet testé pour qu'il soit compilé en un fichier .lib. Ajoutez un projet de test distinct qui référence le projet testé.  
  
 Cette approche présente l'avantage de permettre à vos tests d'utiliser des membres privés mais de conserver les tests dans un projet distinct. Toutefois, elle peut ne pas convenir pour certaines applications où vous devez avoir une bibliothèque de liens dynamiques (.dll).  
  
 Passez à la procédure [Pour changer le code testé en une bibliothèque statique](#staticLink).  
  
 **Les tests unitaires doivent utiliser des données et des fonctions privées, et le code doit être généré sous la forme d’une bibliothèque de liens dynamiques (DLL) :**  
 Ajoutez les tests unitaires dans le même projet que le code du produit.  
  
 Passez à la procédure [Pour ajouter des tests unitaires dans le même projet](#sameProject).  
  
## <a name="creating-the-tests"></a>Créer les tests  
  
### <a name="staticLink"></a> Pour changer le code testé en une bibliothèque statique  
  
- Si vos tests doivent utiliser des membres qui ne sont pas exportés par un projet testé et que le projet de test est généré sous forme d'une bibliothèque dynamique, pensez à le convertir en bibliothèque statique.  
  
  1. Dans l’Explorateur de solutions, dans le menu contextuel du projet testé, choisissez **Propriétés**. La fenêtre des propriétés du projet s'ouvre.  
  
  2. Choisissez **Propriétés de configuration**, **Général**.  
  
  3. Définissez **Type de configuration** sur **Bibliothèque statique (.lib)**.  
  
  Poursuivez avec la procédure [Pour lier les tests aux fichiers objets ou bibliothèques](#objectRef).  
  
### <a name="projectRef"></a> Pour référencer des fonctions exportées depuis le projet de test  
  
- Si un projet testé exporte les fonctions que vous souhaitez tester, vous pouvez ajouter une référence au projet de code à partir du projet de test.  
  
  1. Créez un projet de test C++.  
  
      1. Dans le menu **Fichier**, choisissez **Nouveau**, **Projet**, **Visual C++, Test**, **Projet de test unitaire C++**.  
  
  2. Dans l’Explorateur de solutions, dans le menu contextuel du projet de test, choisissez **Références**. La fenêtre des propriétés du projet s'ouvre.  
  
  3. Sélectionnez **Propriétés communes**, **Structure et références**, puis cliquez sur le bouton **Ajouter une nouvelle référence**.  
  
  4. Sélectionnez **Projets**, puis le projet à tester.  
  
       Choisissez le bouton **Ajouter** .  
  
  5. Dans les propriétés du projet de test, ajoutez l'emplacement du projet testé aux répertoires Include.  
  
       Choisissez **Propriétés de configuration**, **Répertoires VC++**, **Répertoires Include**.  
  
       Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.  
  
  Passez à [Écrire les tests unitaires](#addTests).  
  
### <a name="objectRef"></a> Pour lier les tests aux fichiers objets ou bibliothèques  
  
- Si le code testé n’exporte pas les fonctions que vous souhaitez tester, vous pouvez ajouter le fichier de sortie **.obj** ou **.lib** aux dépendances du projet de test.  
  
  1. Créez un projet de test C++.  
  
      1. Dans le menu **Fichier**, choisissez **Nouveau**, **Projet**, **Visual C++, Test**, **Projet de test unitaire C++**.  
  
  2. Dans l’Explorateur de solutions, dans le menu contextuel du projet de test, choisissez **Propriétés**. La fenêtre des propriétés du projet s'ouvre.  
  
  3. Choisissez **Propriétés de configuration**, **Éditeur de liens**, **Entrée**, **Dépendances supplémentaires**.  
  
       Choisissez **Modifier**, puis ajoutez les noms des fichiers **.obj** ou **.lib**. N’utilisez pas les chemins d’accès complets.  
  
  4. Choisissez **Propriétés de configuration**, **Éditeur de liens**, **Général**, **Répertoires de bibliothèques supplémentaires**.  
  
       Choisissez **Modifier**, puis ajoutez le chemin d’accès au répertoire des fichiers **.obj** ou **.lib**. Le chemin d’accès se trouve généralement dans le dossier de build du projet testé.  
  
  5. Choisissez **Propriétés de configuration**, **Répertoires VC++**, **Répertoires Include**.  
  
       Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.  
  
  Passez à [Écrire les tests unitaires](#addTests).  
  
### <a name="sameProject"></a> Pour ajouter des tests unitaires dans le même projet  
  
1. Modifiez les propriétés du projet du code du produit pour inclure les en-têtes et les fichiers bibliothèques qui sont requis pour le test unitaire.  
  
   1. Dans l'Explorateur de solutions, dans le menu contextuel du projet testé, choisissez Propriétés. La fenêtre des propriétés du projet s'ouvre.  
  
   2. Choisissez **Propriétés de configuration**, **Répertoires VC++**.  
  
   3. Modifiez les répertoires Include et de bibliothèques :  
  
       |||  
       |-|-|  
       |**Répertoires Include**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
       |**Répertoires de bibliothèques**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2. Ajoutez un fichier de test unitaire C++ :  
  
   - Dans l’Explorateur de solutions, dans le menu contextuel du projet, choisissez **Ajouter**, **Nouvel élément**, puis **Test unitaire C++**.  
  
   Passez à [Écrire les tests unitaires](#addTests).  
  
## <a name="addTests"></a> Écrire les tests unitaires  
  
1. Dans chaque fichier de code de test unitaire, ajoutez une instruction `#include` pour les en-têtes du projet testé.  
  
2. Ajoutez les classes et les méthodes de test aux fichiers de code de test unitaire. Exemple :  
  
   ```cpp  
   #include "stdafx.h"  
   #include "CppUnitTest.h"  
   #include "MyProjectUnderTest.h"  
   using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
   namespace MyTest  
   {  
     TEST_CLASS(MyTests)  
     {  
     public:  
         TEST_METHOD(MyTestMethod)  
         {  
             Assert::AreEqual(MyProject::Multiply(2,3), 6);  
         }  
     };  
   }  
   ```  
  
   Pour plus d’informations, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](http://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Exécuter les tests  
  
1. Dans le menu **Affichage** , choisissez **Autres fenêtres**, **Explorateur de tests**.  
  
2. Dans l'Explorateur de tests, choisissez **Exécuter tout**.  
  
   Pour plus d’informations, consultez [démarrage rapide : Développement avec l’Explorateur de tests piloté par test](../test/quick-start-test-driven-development-with-test-explorer.md).
