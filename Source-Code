#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>
#include <stdlib.h>
#include <time.h>

#define BUFFER_SIZE 5
#define NUM_ITEMS 5

int buffer[BUFFER_SIZE];
int in = 0, out = 0;

sem_t mutex, empty, full;

void *producer(void *arg) {
    int id = *(int *)arg;

    for(int i = 0; i < NUM_ITEMS; i++) {
        int item = rand() % 100;

        sem_wait(&empty);
        sem_wait(&mutex);

        int position = in;
        buffer[in] = item;
        in = (in + 1) % BUFFER_SIZE;

        printf("Producer %d produced item %d at position %d\n", id, item, position);

        sem_post(&mutex);
        sem_post(&full);
    }

    return NULL;
}

void *consumer(void *arg) {
    int id = *(int *)arg;

    for(int i = 0; i < NUM_ITEMS; i++) {

        sem_wait(&full);
        sem_wait(&mutex);

        int position = out;
        int item = buffer[out];
        out = (out + 1) % BUFFER_SIZE;

        printf("Consumer %d consumed item %d from position %d\n", id, item, position);

        sem_post(&mutex);
        sem_post(&empty);
    }

    return NULL;
}

int main() {

    pthread_t producers[2], consumers[2];
    int prod_id[2] = {1,2};
    int cons_id[2] = {1,2};

    srand(time(NULL));

    sem_init(&mutex, 0, 1);
    sem_init(&empty, 0, BUFFER_SIZE);
    sem_init(&full, 0, 0);

    for(int i=0;i<2;i++)
        pthread_create(&producers[i], NULL, producer, &prod_id[i]);

    for(int i=0;i<2;i++)
        pthread_create(&consumers[i], NULL, consumer, &cons_id[i]);

    for(int i=0;i<2;i++)
        pthread_join(producers[i], NULL);

    for(int i=0;i<2;i++)
        pthread_join(consumers[i], NULL);

    sem_destroy(&mutex);
    sem_destroy(&empty);
    sem_destroy(&full);

    return 0;
}
