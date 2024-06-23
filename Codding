#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 5

typedef struct {
    char nim[7];
    char nama[50];
    float nilai;
    char hasil[20]; // "lulus" atau "tidak lulus"
} Siswa;

typedef struct {
    Siswa items[MAX];
    int front;
    int rear;
} Queue;

void initializeQueue(Queue *q) {
    q->front = -1;
    q->rear = -1;
}

int isFull(Queue *q) {
    return q->rear == MAX - 1;
}

int isEmpty(Queue *q) {
    return q->front == -1;
}

void enqueue(Queue *q) {
    Siswa siswa;
    printf("Masukkan NIM (6 digit): ");
    scanf("%s", siswa.nim);
    getchar(); // untuk menangkap newline character setelah input nim

    printf("Masukkan nama siswa: ");
    fgets(siswa.nama, sizeof(siswa.nama), stdin);
    siswa.nama[strcspn(siswa.nama, "\n")] = '\0'; // menghapus newline character dari input nama

    printf("Masukkan nilai siswa: ");
    scanf("%f", &siswa.nilai);
    getchar(); // untuk menangkap newline character setelah input nilai

    if (siswa.nilai > 65.00) {
        strcpy(siswa.hasil, "lulus");
    } else {
        strcpy(siswa.hasil, "tidak lulus");
    }

    if (isFull(q)) {
        printf("Antrian penuh!\n");
    } else {
        if (q->front == -1) q->front = 0;
        q->rear++;
        q->items[q->rear] = siswa;
        printf("Data siswa berhasil dimasukkan ke dalam antrian.\n");
    }
}

void dequeue(Queue *q) {
    if (isEmpty(q)) {
        printf("Antrian kosong!\n");
    } else {
        printf("Data siswa yang dihapus:\n");
        printf("NIM: %s\n", q->items[q->front].nim);
        printf("Nama: %s\n", q->items[q->front].nama);
        printf("Nilai: %.2f\n", q->items[q->front].nilai);
        printf("Hasil: %s\n", q->items[q->front].hasil);

        q->front++;
        if (q->front > q->rear) {
            q->front = q->rear = -1;
        }
    }
}

void display(Queue *q) {
    int i;
    if (isEmpty(q)) {
        printf("Antrian kosong!\n");
    } else {
        printf("Data seluruh siswa dalam antrian:\n");
        for (i = q->front; i <= q->rear; i++) {
            printf("NIM: %s\n", q->items[i].nim);
            printf("Nama: %s\n", q->items[i].nama);
            printf("Nilai: %.2f\n", q->items[i].nilai);
            printf("Hasil: %s\n", q->items[i].hasil);
            printf("\n");
        }
    }
}

int main() {
    Queue q;
    initializeQueue(&q);

    int pilihan;

    do {
        printf("\nMenu:\n");
        printf("1. Masukkan data siswa\n");
        printf("2. Hapus data siswa\n");
        printf("3. Tampilkan data seluruh siswa dalam antrian\n");
        printf("4. Keluar\n");
        printf("Pilih opsi: ");
        scanf("%d", &pilihan);
        getchar(); // untuk menangkap newline character setelah input pilihan

        switch (pilihan) {
            case 1:
                enqueue(&q);
                break;
            case 2:
                dequeue(&q);
                break;
            case 3:
                display(&q);
                break;
            case 4:
                printf("Program selesai.\n");
                break;
            default:
                printf("Opsi tidak valid.\n");
        }

    } while (pilihan != 4);

    return 0;
}
