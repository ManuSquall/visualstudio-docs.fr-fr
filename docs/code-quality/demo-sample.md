---
title: Exemple de projet C++ pour l’analyse du code
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 071c16267486e1dda1e183cad3c488345974a3cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745923"
---
# <a name="sample-c-project-for-code-analysis"></a>Exemple de projet C++ pour l’analyse du code

Les procédures suivantes vous montrent comment créer l’exemple pour la [procédure pas à pas :C++ analyser C/code pour les défauts](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Les procédures créent :

- Une solution Visual Studio nommée CppDemo.

- Un projet de bibliothèque statique nommé CodeDefects.

- Un projet de bibliothèque statique nommé Annotations.

Les procédures fournissent également le code pour les fichiers d’en-tête et *.cpp* pour les bibliothèques statiques.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Créer la solution CppDemo et le projet CodeDefects

1. Cliquez sur le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Nouveau projet**.

2. Dans la liste d’arborescence des **types** de C++ projets, si n’est pas votre langue par défaut dans vs, développez **autres langues**.

3. Développez **Visual C++** , puis cliquez sur **Général**.

4. Dans **Modèles**, cliquez sur **Projet vide**.

5. Dans la zone de texte **Nom**, tapez **CodeDefects**.

6. Cochez la case **Créer le répertoire pour la solution**.

7. Dans la zone de texte **Nom de la solution**, tapez **CppDemo**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurer le projet CodeDefects comme bibliothèque statique

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **CodeDefects**, puis cliquez sur **Propriétés**.

2. Développez **Propriétés de configuration**, puis cliquez sur **Général**.

3. Dans la liste **Général**, sélectionnez le texte dans la colonne en regard d’**Extension cible** et tapez **.lib**.

4. Dans **Paramètres par défaut du projet** , cliquez sur la colonne en regard de **Type de configuration**, puis cliquez sur **Bibliothèque statique (.lib)** .

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Ajouter le fichier source et d’en-tête au projet CodeDefects

1. Dans l’Explorateur de solutions, développez **CodeDefects**, cliquez avec le bouton droit sur **Fichiers d’en-tête**, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Code**, puis sur **Fichier d’en-tête (.h)** .

3. Dans le champ **Nom**, tapez **Bug.h**, puis cliquez sur **Ajouter**.

4. Copiez le code suivant et collez-le dans le fichier *Bug.h* dans l’éditeur Visual Studio.

    ```cpp
    #include <windows.h>

    //
    //These 3 functions are consumed by the sample
    //  but are not defined. This project cannot be linked!
    //

    bool CheckDomain( LPCSTR );
    HRESULT ReadUserAccount();

    //
    //These constants define the common sizes of the
    //  user account information throughout the program
    //

    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

5. Dans l’Explorateur de solutions, cliquez sur **Fichiers sources**, pointez sur **Nouveau**, puis cliquez sur **Nouvel élément**.

6. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Fichier C++ (.cpp)** .

7. Dans le champ **Nom**, tapez **Bug.cpp**, puis cliquez sur **Ajouter**.

8. Copiez le code suivant et collez-le dans le fichier *Bug.cpp* dans l’éditeur Visual Studio.

    ```cpp
    #include <stdlib.h>
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount() )
        {

            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )
            {
                if ( g_userAccount[len] == '\\' )
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete [] domain;
                return false;
            }
            else
            {
                domain[len]='\0';
            }
            // Process domain string
            bool result = CheckDomain( domain );

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i+j;
    }
    ```

9. Cliquez sur le menu **Fichier**, puis sur **Enregistrer tout**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ajouter le projet Annotations et le configurer comme bibliothèque statique

1. Dans l’Explorateur de solutions, cliquez sur **CppDemo**, pointez sur **Ajouter** et cliquez sur **Nouveau projet**.

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez Visual C++, cliquez sur **Général**, puis sur **Projet vide**.

3. Dans la zone de texte **Nom**, tapez **Annotations**, puis cliquez sur **Ajouter**.

4. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Annotations**, puis cliquez sur **Propriétés**.

5. Développez **Propriétés de configuration**, puis cliquez sur **Général**.

6. Dans la liste **Général**, sélectionnez le texte dans la colonne en regard d’**Extension cible** et tapez **.lib**.

7. Dans **Paramètres par défaut du projet** , cliquez sur la colonne en regard de **Type de configuration**, puis cliquez sur **Bibliothèque statique (.lib)** .

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Ajouter le fichier d’en-tête et le fichier source au projet Annotations

1. Dans l’Explorateur de solutions, développez **Annotations**, cliquez avec le bouton droit sur **Fichiers d’en-tête**, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Fichier d’en-tête (.h)** .

3. Dans la zone **Nom**, tapez **annotations.h**, puis cliquez sur **Ajouter**.

4. Copiez le code suivant et collez-le dans le fichier *annotations.h* dans l’éditeur Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5. Dans l’Explorateur de solutions, cliquez sur **Fichiers sources**, pointez sur **Nouveau**, puis cliquez sur **Nouvel élément**.

6. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Code** et sur **Fichier C++ (.cpp)** .

7. Dans la zone **Nom**, tapez **annotations.cpp**, puis cliquez sur **Ajouter**.

8. Copiez le code suivant et collez-le dans le fichier *annotations.cpp* dans l’éditeur Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>
    #include <windows.h>
    #include <stdlib.h>
    #include "annotations.h"

    LinkedList* AddTail( LinkedList *node, int value )
    {
        LinkedList *newNode = NULL;

        // finds the last node
        while ( node->next != NULL )
        {
            node = node->next;
        }

        // appends the new node
        newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }

    ```

9. Cliquez sur le menu **Fichier**, puis sur **Enregistrer tout**.
