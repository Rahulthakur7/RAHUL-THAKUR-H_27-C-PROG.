# RAHUL-THAKUR-H_27-C-PROG.
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int choice;
    char filename[20];
    FILE *fp;

    while(1)
    {
        printf("\n1. Create a file");
        printf("\n2. Delete a file");
        printf("\n3. Modify a file");
        printf("\n4. Exit");
        printf("\nEnter your choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                printf("\nEnter the name of the file to create: ");
                scanf("%s", filename);
                fp = fopen(filename, "w");
                if(fp == NULL)
                {
                    printf("\nError creating file!");
                    exit(1);
                }
                printf("\nFile created successfully!");
                fclose(fp);
                break;

            case 2:
                printf("\nEnter the name of the file to delete: ");
                scanf("%s", filename);
                if(remove(filename) == 0)
                {
                    printf("\nFile deleted successfully!");
                }
                else
                {
                    printf("\nError deleting file!");
                    exit(1);
                }
                break;

            case 3:
                printf("\nEnter the name of the file to modify: ");
                scanf("%s", filename);
                fp = fopen(filename, "a+");
                if(fp == NULL)
                {
                    printf("\nError opening file!");
                    exit(1);
                }
                char content[100];
                printf("\nEnter the content to add to the file: ");
                scanf("%s", content);
                fprintf(fp, "%s", content);
                fclose(fp);
                printf("\nContent added successfully!");
                break;

            case 4:
                exit(0);

            default:
                printf("\nInvalid choice!");
        }
    }

    return 0;
}
