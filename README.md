# -Resume-Builder
    #include <stdio.h>

    int main() {
    FILE *fp;
    int choice;
    char data[200];

    printf("1. Create Resume\n2. View Resume\n3. Add Details\n");
    scanf("%d", &choice);
    getchar(); 

    if (choice == 1) {
        fp = fopen("resume.txt", "w");
        printf("Enter details: ");
        fgets(data, 200, stdin);
        fprintf(fp, "%s", data);
        fclose(fp);
        printf("Resume Created.\n");
    }
    else if (choice == 2) {
        fp = fopen("resume.txt", "r");
        if (!fp) { printf("Resume not found!\n"); return 0; }
        printf("--- Resume ---\n");
        while (fgets(data, 200, fp)) printf("%s", data);
        fclose(fp);
    }
    else if (choice == 3) {
        fp = fopen("resume.txt", "a");
        if (!fp) { printf("Resume not found!\n"); return 0; }
        printf("Enter more details: ");
        fgets(data, 200, stdin);
        fprintf(fp, "%s", data);
        fclose(fp);
        printf("Details Added.\n");
    }
    else {
        printf("Invalid choice!");
    }

    return 0;
}
