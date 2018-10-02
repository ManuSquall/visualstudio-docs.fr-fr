---
title: 'Procédure pas à pas : Analyse du Code C-C++ pour rechercher les erreurs | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1c944a50330f458240b3da2fea8952abb5b8f02b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494456"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas : analyse du code C/C++ pour rechercher les erreurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : analyse du Code C/C++ pour rechercher les erreurs](https://docs.microsoft.com/visualstudio/code-quality/walkthrough-analyzing-c-cpp-code-for-defects).  
  
Cette procédure pas à pas montre comment analyser des défauts de code potentiels du code C/C++ à l’aide de l’outil d’analyse de code pour le code C/C++.  
  
 Dans cette procédure pas à pas, vous parcourez le processus de l’utilisation de l’analyse du code pour analyser votre code C/C++ pour rechercher les erreurs de code potentiels.  
  
 Vous allez effectuer les étapes suivantes :  
  
-   Exécuter l’analyse du code sur le code natif.  
  
-   Analyser les avertissements d’erreur de code.  
  
-   Traiter l’avertissement comme une erreur.  
  
-   Annoter le code source pour améliorer l’analyse des erreurs de code.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] ou [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
-   Une copie de la [exemple de démonstration](../code-quality/demo-sample.md).  
  
-   Compréhension élémentaire de C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des erreurs de code sur le code natif  
  
1.  Ouvrez la solution de démonstration dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     La solution de démonstration remplit désormais **l’Explorateur de solutions**.  
  
2.  Sur le **Build** menu, cliquez sur **régénérer la Solution**.  
  
     La solution se génère sans erreurs ni avertissements.  
  
3.  Dans **l’Explorateur de solutions**, sélectionnez le projet CodeDefects.  
  
4.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     Le **Pages de propriétés de CodeDefects** boîte de dialogue s’affiche.  
  
5.  Cliquez sur **analyse du Code**.  
  
6.  Cliquez sur le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.  
  
7.  Régénérez le projet CodeDefects.  
  
     Avertissements d’analyse du code sont affichés dans le **liste d’erreurs**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Pour analyser les avertissements d’erreur de code  
  
1.  Sur le **vue** menu, cliquez sur **liste d’erreurs**.  
  
     Selon le profil de développeur que vous avez choisi dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous devrez peut-être pointer vers **Windows autres** sur le **vue** menu, puis sur **liste d’erreurs**.  
  
2.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6230 : cast implicite entre types sémantiquement différents : utilisation de HRESULT dans un contexte Boolean.  
  
     L’éditeur de code affiche la ligne qui a provoqué l’avertissement dans la fonction `bool``ProcessDomain()`. Cet avertissement indique qu’une valeur HRESULT est utilisé dans une instruction 'if' où un résultat booléen est attendu.  
  
3.  Corriger cet avertissement à l’aide de la macro SUCCEEDED. Votre code doit ressembler au code suivant :  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6282 : opérateur Incorrect : assignation à la constante dans un contexte de test. == Est-il intentionnel ?  
  
5.  Corriger cet avertissement en testant l’égalité. Votre code doit ressembler au code suivant :  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Pour traiter un avertissement comme une erreur  
  
1.  Dans le fichier Bug.cpp, ajoutez le code suivant `#pragma` instruction au début du fichier à traiter l’avertissement C6001 comme une erreur :  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Régénérez le projet CodeDefects.  
  
     Dans le **liste d’erreurs**, C6001 apparaît maintenant comme une erreur.  
  
3.  Corrigez les deux erreurs C6001 restantes dans le **liste d’erreurs** en initialisant `i` et `j` à 0.  
  
4.  Régénérez le projet CodeDefects.  
  
     Le projet est généré sans les avertissements ou erreurs.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation de code source dans annotation.c  
  
1.  Dans l’Explorateur de solutions, sélectionnez le projet d’Annotations.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     Le **Pages de propriétés d’Annotations** boîte de dialogue s’affiche.  
  
3.  Cliquez sur **analyse du Code**.  
  
4.  Sélectionnez le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.  
  
5.  Régénérez le projet Annotations.  
  
6.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6011 : déréférencement de pointeur NULL 'newNode'.  
  
     Cet avertissement indique que l’appelant pour vérifier la valeur de retour. Dans ce cas, un appel à **AllocateNode** peut retourner une valeur NULL (consultez le fichier d’en-tête annotations.h la déclaration de fonction d’AllocateNode).  
  
7.  Ouvrez le fichier annotations.cpp.  
  
8.  Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Régénérez le projet Annotations.  
  
     Le projet est généré sans les avertissements ou erreurs.  
  
### <a name="to-use-source-code-annotation"></a>Pour utiliser l’annotation de code source  
  
1.  Annoter des paramètres formels et la valeur de retour de la fonction `AddTail` en utilisant les conditions de pré-script et post-script comme indiqué dans cet exemple :  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Régénérez le projet Annotations.  
  
3.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6011 : suppression de référence pointeur NULL 'node'.  
  
     Cet avertissement indique que le nœud passé dans la fonction peut être null et indique le numéro de ligne où l’avertissement a été déclenché.  
  
4.  Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Régénérez le projet Annotations.  
  
     Le projet est généré sans les avertissements ou erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : analyse du code managé pour les erreurs de code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)



