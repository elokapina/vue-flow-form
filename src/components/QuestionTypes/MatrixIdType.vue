<script>
  /*
    Copyright (c) 2020 - present, DITDOT Ltd. - MIT Licence
    https://github.com/ditdot-dev/vue-flow-form
    https://www.ditdot.hr/en
  */

  import TextType from './TextType.vue'
  import { QuestionType } from '../../models/QuestionModel'

  export default {
    extends: TextType,
    name: QuestionType.MatrixId,
    methods: {
      validate() {
        if (this.hasValue) {
          // https://matrix.org/docs/spec/appendices#identifier-grammar
          // Actually upper-case characters are not allowed in the local part, but we might want to accept and downcase
          // them. Or maybe the server does it automatically?
          return /^@[0-9a-zA-Z.=_/-]+:[0-9a-zA-Z:.-]+$/.test(this.dataValue)
        }

        return !this.question.required
      }
    }
  }
</script>
