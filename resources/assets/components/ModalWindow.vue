<template>
        <div id="modal" :class="{ show: modalOpen }">
            <button class="modal-close" @click="modalOpen = false">&times;</button>
            <div class="modal-content">
                <slot></slot>
            </div>
        </div>
</template>
<script>
    export default {
        data() {
            return {
                modalOpen: false
            }
        },
        methods: {
            escapeKeyListener( evt ) {
                if ( evt.keyCode === 27 && this.modalOpen ) {
                    this.modalOpen = false;
                }
            }
        },
        watch: {
            modalOpen: function() {
                var className = 'modal-open';
                if ( this.modalOpen ) {
                    document.body.classList.add( className );
                } else {
                    document.body.classList.remove( className );
                }
            }
        },
        created: function() {
            document.addEventListener( 'keyup', this.escapeKeyListener );
        },
        destroyed: function() {
            document.removeEventListener( 'keyup', this.escapeKeyListener );
        }

    }
</script>
