---
title: "Écrire des tests unitaires pour des DLL C++ dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: e6749d79749c8a3f3b6bb74c946841a69e432f4d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Écrire des tests unitaires pour des DLL C++ dans Visual Studio

 Il existe plusieurs façons de tester du code de DLL, selon qu’elle exporte ou non les fonctions que vous voulez tester. Choisissez l'un des moyens suivants :  
  
 **Les tests unitaires appellent seulement des fonctions exportées depuis la DLL :**  
 Ajoutez un projet de test distinct, comme décrit dans [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md). Dans le projet de test, ajoutez une référence au projet DLL.  
  
 Passez à la procédure [Pour référencer des fonctions exportées depuis le projet DLL](#projectRef).  
  
 **La DLL est générée sous la forme d’un fichier .exe :**  
 Ajoutez un projet de test distinct. Liez-le au fichier objet de sortie.  
  
 Passez à la procédure [Pour lier les tests aux fichiers objets ou bibliothèques](#objectRef).  
  
 **Les tests unitaires appellent des fonctions non-membres qui ne sont pas exportées depuis la DLL, et la DLL peut être générée sous forme de bibliothèque statique :**  
 Modifiez le projet DLL pour qu’il soit compilé sous forme de fichier .lib. Ajoutez un projet de test distinct qui référence le projet testé.  
  
 Cette approche présente l’avantage de permettre à vos tests d’utiliser des membres non exportés, mais de conserver les tests dans un projet distinct.  
  
 Passez à la procédure [Pour changer la DLL en une bibliothèque statique](#staticLink).  
  
 **Les tests unitaires doivent appeler des fonctions non-membres qui ne sont pas exportées, et le code doit être généré sous la forme d’une bibliothèque de liens dynamiques (DLL) :**  
 Ajoutez les tests unitaires dans le même projet que le code du produit.  
  
 Passez à la procédure [Pour ajouter des tests unitaires dans le même projet](#sameProject).  
  
## <a name="creating-the-tests"></a>Créer les tests  
  
###  <a name="staticLink"></a> Pour changer la DLL en une bibliothèque statique  
  
-   Si vos tests doivent utiliser des membres qui ne sont pas exportés par le projet DLL et que le projet de test est généré sous forme d’une bibliothèque dynamique, envisagez de le convertir en bibliothèque statique.  
  
    1.  Dans **l’Explorateur de solutions**, dans le menu contextuel du projet testé, choisissez **Propriétés**. La fenêtre des propriétés du projet s'ouvre.  
  
    2.  Choisissez **Propriétés de configuration | Général**.  
  
    3.  Définissez **Type de configuration** sur **Bibliothèque statique (.lib)**.  
  
 Poursuivez avec la procédure [Pour lier les tests aux fichiers objets ou bibliothèques](#objectRef).  
  
###  <a name="projectRef"></a> Pour référencer des fonctions de DLL exportées depuis le projet de test  
  
-   Si un projet DLL exporte les fonctions que vous voulez tester, vous pouvez ajouter une référence au projet de code depuis le projet de test.  
  
    1.  Créez un projet de test unitaire natif.  
  
        1.  Dans le menu **Fichier**, choisissez **Nouveau | Projet | Visual C++ | Test | Projet de test unitaire C++**.  
  
    2.  Dans **l’Explorateur de solutions**, dans le menu contextuel du projet de test, choisissez **Références**. La fenêtre des propriétés du projet s'ouvre.  
  
    3.  Sélectionnez **Propriétés communes | Structure et références**, puis cliquez sur le bouton **Ajouter une nouvelle référence**.  
  
    4.  Sélectionnez **Projets**, puis le projet à tester.  
  
         Choisissez le bouton **Ajouter** .  
  
    5.  Dans les propriétés du projet de test, ajoutez l'emplacement du projet testé aux répertoires Include.  
  
         Choisissez **Propriétés de configuration | Répertoires VC++ | Répertoires Include**.  
  
         Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.  
  
 Passez à [Écrire les tests unitaires](#addTests).  
  
###  <a name="objectRef"></a> Pour lier les tests aux fichiers objets ou bibliothèques  
  
-   Si la DLL n’exporte pas les fonctions que vous voulez tester, vous pouvez ajouter le fichier de sortie **.obj** ou **.lib** aux dépendances du projet de test.  
  
    1.  Créez un projet de test unitaire natif.  
  
        1.  Dans le menu **Fichier**, choisissez **Nouveau | Projet | Visual C++ | Test | Projet de test unitaire natif**.  
  
    2.  Dans **l’Explorateur de solutions**, dans le menu contextuel du projet de test, choisissez **Propriétés**.  
  
    3.  Choisissez **Propriétés de configuration | Éditeur de liens | Entrée | Dépendances supplémentaires**.  
  
         Choisissez **Modifier**, puis ajoutez les noms des fichiers **.obj** ou **.lib**. N’utilisez pas les chemins d’accès complets.  
  
    4.  Choisissez **Propriétés de configuration | Éditeur de liens | Général | Répertoires de bibliothèques supplémentaires**.  
  
         Choisissez **Modifier**, puis ajoutez le chemin d’accès au répertoire des fichiers **.obj** ou **.lib**. Le chemin d’accès se trouve généralement dans le dossier de build du projet testé.  
  
    5.  Choisissez **Propriétés de configuration | Répertoires VC++ | Répertoires Include**.  
  
         Choisissez **Modifier**, puis ajoutez le répertoire d’en-tête du projet testé.  
  
 Passez à [Écrire les tests unitaires](#addTests).  
  
###  <a name="sameProject"></a> Pour ajouter des tests unitaires dans le même projet  
  
1.  Modifiez les propriétés du projet du code du produit pour inclure les en-têtes et les fichiers bibliothèques qui sont requis pour le test unitaire.  
  
    1.  Dans **l’Explorateur de solutions**, dans le menu contextuel du projet testé, choisissez Propriétés. La fenêtre des propriétés du projet s'ouvre.  
  
    2.  Choisissez **Propriétés de configuration | Répertoires VC++**.  
  
    3.  Modifiez les répertoires Include et de bibliothèques :  
  
        |||  
        |-|-|  
        |**Répertoires Include** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
        |**Répertoires de bibliothèques** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2.  Ajoutez un fichier de test unitaire C++ :  
  
    -   Dans **l’Explorateur de solutions**, dans le menu contextuel du projet, choisissez **Ajouter | Nouvel élément | Test unitaire C++**.  
  
 Passez à [Écrire les tests unitaires](#addTests).  
  
##  <a name="addTests"></a> Écrire les tests unitaires  
  
1.  Dans chaque fichier de code de test unitaire, ajoutez une instruction `#include` pour les en-têtes du projet testé.  
  
2.  Ajoutez les classes et les méthodes de test aux fichiers de code de test unitaire. Exemple :  
  
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
  
## <a name="run-the-tests"></a>Exécuter les tests  
  
1.  Dans le menu **Test**, choisissez **Fenêtres | Explorateur de tests**.  
2. Si tous vos tests ne sont pas visibles dans la fenêtre, générez le projet de test en cliquant avec le bouton droit sur son nœud dans **l’Explorateur de solutions** et en choisissant **Générer** ou **Régénérer**.
  
2.  Dans l’Explorateur de tests, choisissez **Exécuter tout** ou sélectionnez les tests spécifiques à exécuter. Cliquez avec le bouton droit sur un test pour accéder à d’autres options, notamment son exécution en mode débogage avec des points d’arrêt activés.
  
## <a name="see-also"></a>Voir aussi
[Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)

  
## <a name="see-also"></a>Voir aussi  
 [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)   
 [Informations de référence sur l’API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)   
 [Importation et exportation](/cpp/build/importing-and-exporting)
